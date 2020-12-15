---
title: Wcf 開発者向けの gRPC-gRPC への WCF 要求/応答サービスの移行
description: 単純な要求/応答サービスを WCF から gRPC に移行する方法について説明します。
ms.date: 09/02/2019
ms.openlocfilehash: 29a7bc77bc3a4becd767fc7a50adff5b746f54bc
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512698"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a>WCF 要求/応答サービスを gRPC 単項 RPC に移行する

このセクションでは、WCF の基本的な要求/応答サービスを ASP.NET Core gRPC の単項 RPC サービスに移行する方法について説明します。 これらのサービスは、Windows Communication Foundation (WCF) と gRPC の両方で最も単純なサービスの種類であるため、開始するのが優れた場所です。 サービスを移行した後、同じファイルからクライアントライブラリを生成して、 `.proto` .net クライアントアプリケーションからサービスを使用する方法を学習します。

## <a name="the-wcf-solution"></a>WCF ソリューション

[PortfoliosSample ソリューション](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys)には、単一のポートフォリオまたは特定の商人のすべてのポートフォリオをダウンロードする単純な要求/応答ポートフォリオサービスが含まれています。 サービスは、インターフェイスで属性を使用して定義され `IPortfolioService` `ServiceContract` ます。

```csharp
[ServiceContract]
public interface IPortfolioService
{
    [OperationContract]
    Task<Portfolio> Get(Guid traderId, int portfolioId);

    [OperationContract]
    Task<List<Portfolio>> GetAll(Guid traderId);
}
```

`Portfolio`モデルは、 [DataContract](xref:System.Runtime.Serialization.DataContractAttribute)でマークされた単純な C# クラスであり、オブジェクトのリストを含み `PortfolioItem` ます。 これらのモデルは、 `TraderSys.PortfolioData` データアクセスの抽象化を表すリポジトリクラスと共にプロジェクトで定義されます。

```csharp
[DataContract]
public class Portfolio
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public Guid TraderId { get; set; }

    [DataMember]
    public List<PortfolioItem> Items { get; set; }
}

[DataContract]
public class PortfolioItem
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public int ShareId { get; set; }

    [DataMember]
    public int Holding { get; set; }

    [DataMember]
    public decimal Cost { get; set; }
}
```

`ServiceContract`実装では、型のインスタンスを返す依存関係の挿入によって提供されるリポジトリクラスを使用し `DataContract` ます。

```csharp
public class PortfolioService : IPortfolioService
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }

    public async Task<Portfolio> Get(Guid traderId, int portfolioId)
    {
        return await _repository.GetAsync(traderId, portfolioId);
    }

    public async Task<List<Portfolio>> GetAll(Guid traderId)
    {
        return await _repository.GetAllAsync(traderId);
    }
}
```

## <a name="the-portfoliosproto-file"></a>ポートフォリオのプロトコルファイル

前のセクションの手順に従っている場合は、次のようなファイルを含む gRPC プロジェクトが必要 `portfolios.proto` です。

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

最初の手順では、 `DataContract` クラスを同等の Protobuf に移行します。

## <a name="convert-the-datacontract-classes-to-grpc-messages"></a>DataContract クラスを gRPC メッセージに変換します

クラスが依存して `PortfolioItem` いるため、クラスは最初に Protobuf メッセージに変換され `Portfolio` ます。 クラスは単純で、3つのプロパティは gRPC データ型に直接マップされます。 `Cost`購入時の共有に対して支払われた価格を表すプロパティは、 `decimal` フィールドです。 gRPC で `float` は、または `double` の実数のみがサポートされており、通貨には適していません。 共有価格は最低1セントであるため、コストはセントとして表現でき `int32` ます。

> [!NOTE]
> `snake_case`ファイル内のフィールド名には必ずを使用してください `.proto` 。 C# コードジェネレーターはそれらをに変換します `PascalCase` 。他の言語のユーザーは、さまざまなコーディング基準を使用することに感謝します。

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 share_id = 2;
    int32 holding = 3;
    int32 cost_cents = 4;
}
```

`Portfolio`クラスは少し複雑です。 WCF コードでは、開発者はプロパティとしてを使用し、を `Guid` `TraderId` 格納し `List<PortfolioItem>` ます。 ファーストクラスの型を持たない Protobuf で `UUID` は、フィールドにを使用して、独自の `string` コードで解析する必要があり `traderId` ます。 項目の一覧については、 `repeated` フィールドでキーワードを使用します。

```protobuf
message Portfolio {
    int32 id = 1;
    string trader_id = 2;
    repeated PortfolioItem items = 3;
}
```

データメッセージを取得したので、サービス RPC エンドポイントを宣言できます。

## <a name="convert-servicecontract-to-a-grpc-service"></a>ServiceContract を gRPC サービスに変換する

WCF メソッドは、 `Get` との2つのパラメーターを受け取ります `Guid traderId` `int portfolioId` 。 gRPC サービスメソッドは、1つのパラメーターのみを受け取ることができるため、2つの値を格納するメッセージを作成する必要があります。 これらの要求オブジェクトには、メソッドと同じ名前を付け、その後にサフィックスを付けるのが一般的です `Request` 。 ここで `string` も、はではなくフィールドに使用されてい `traderId` `Guid` ます。

サービスはメッセージを直接返すこともできました `Portfolio` が、今後は旧バージョンとの互換性に影響する可能性があります。 サービスのメソッドごとに個別のメッセージとメッセージを定義することをお勧めし `Request` `Response` ます。これは、その多くが同じであっても同じです。 そのため、 `GetResponse` 1 つのフィールドを含むメッセージを宣言 `Portfolio` します。

次の例では、gRPC サービスメソッドの宣言を次のメッセージと共に示し `GetRequest` ます。

```protobuf
message GetRequest {
    string trader_id = 1;
    int32 portfolio_id = 2;
}

message GetResponse {
    Portfolio portfolio = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (GetResponse);
}
```

WCF メソッドは、 `GetAll` 1 つのパラメーターのみを受け取るの `traderId` で、 `string` パラメーターの型としてを指定できます。 ただし、gRPC には定義済みのメッセージ型が必要です。 この要件は、今後の旧バージョンとの互換性のために、すべての入力と出力にカスタムメッセージを使用する方法を適用するのに役立ちます。

また、WCF メソッドはを返します `List<Portfolio>` が、同じ理由で単純なパラメーターの型を許可しないため、gRPC は `repeated Portfolio` 戻り値の型としてを許可しません。 代わりに、リストを `GetAllResponse` ラップする型を作成します。

> [!WARNING]
> メッセージを作成 `PortfolioList` したり、類似したものを複数のサービスメソッドで使用したりすることがありますが、このようなことは避けてください。 サービスのさまざまなメソッドがどのように進化しているかを知ることはできません。そのため、メッセージを明確にして明確に分離することができます。

```protobuf
message GetAllRequest {
    string trader_id = 1;
}

message PortfolioList {
    repeated Portfolio portfolios = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (Portfolio);
    rpc GetAll(GetAllRequest) returns (GetAllResponse);
}
```

これらの変更を使用してプロジェクトを保存すると、gRPC ビルドターゲットがバックグラウンドで実行され、すべての Protobuf メッセージ型と、サービスを実装するために継承できる基本クラスが生成されます。

クラスを開き、 `Services/GreeterService.cs` コード例を削除します。 これで、ポートフォリオサービスの実装を追加できるようになりました。 生成された基底クラスは名前空間にあり、 `Protos` 入れ子になったクラスとして生成されます。 gRPC は、ファイル内のサービスと同じ名前の静的クラス `.proto` と、その静的クラス内のサフィックスを持つ基底クラスを作成し `Base` ます。そのため、基本データ型の完全な識別子はに `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase` なります。

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

基底クラスは、 `virtual` サービスを `Get` `GetAll` 実装するためにオーバーライドできるおよびのメソッドを宣言します。 メソッドは、実装していない場合は、 `virtual` `abstract` 通常の `Unimplemented` `NotImplementedException` C# コードでをスローするのと同様に、サービスが明示的な grpc ステータスコードを返すことができるようにするためのものではありません。

ASP.NET Core 内のすべての gRPC 単項サービスメソッドの署名が一貫しています。 2つのパラメーターがあります。1つ目は、ファイルで宣言されたメッセージ型、 `.proto` 2 番目のパラメーターは `ServerCallContext` 、ASP.NET Core のと同様に機能するです `HttpContext` 。 実際に `GetHttpContext` は、基になるを取得するために使用できるクラスに対してという拡張メソッドがありますが、 `ServerCallContext` `HttpContext` 頻繁に使用する必要はありません。 `ServerCallContext`この章で後ほど説明します。また、認証についての章もご覧ください。

メソッドの戻り値の型はです `Task<T>` 。ここで、 `T` は応答メッセージの種類です。 すべての gRPC サービスメソッドは非同期です。

## <a name="migrate-the-portfoliodata-library-to-net-core"></a>PortfolioData ライブラリを .NET Core に移行する

この時点で、プロジェクトには、WCF ソリューションのクラスライブラリに含まれるポートフォリオリポジトリとモデルが必要 `TraderSys.PortfolioData` です。 新しいクラスライブラリを作成する最も簡単な方法は、Visual Studio の [ **新しいプロジェクト** ] ダイアログボックスをクラスライブラリ (.NET Standard) テンプレートと共に使用するか、コマンドラインから .NET Core CLI を使用して、ファイルが格納されているディレクトリから次のコマンドを実行し `TraderSys.sln` ます。

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

ライブラリを作成してソリューションに追加したら、生成されたファイルを削除 `Class1.cs` し、ファイルを WCF ソリューションのライブラリから新しいクラスライブラリのフォルダーにコピーして、フォルダー構造を維持します。

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

SDK スタイルの .NET プロジェクト `.cs` では、または独自のディレクトリにあるファイルが自動的にインクルードされるため、プロジェクトに明示的に追加する必要はありません。 残りの手順は、クラスと属性を削除して、 `DataContract` `DataMember` 従来の C# クラスである `Portfolio` `PortfolioItem` ようにすることです。

```csharp
public class Portfolio
{
    public int Id { get; set; }
    public Guid TraderId { get; set; }
    public List<PortfolioItem> Items { get; set; }
}

public class PortfolioItem
{
    public int Id { get; set; }
    public int ShareId { get; set; }
    public int Holding { get; set; }
    public decimal Cost { get; set; }
}
```

## <a name="use-aspnet-core-dependency-injection"></a>ASP.NET Core 依存関係の挿入の使用

このライブラリへの参照を gRPC アプリケーションプロジェクトに追加し、 `PortfolioRepository` grpc サービス実装で依存関係の挿入を使用してクラスを使用できるようになりました。 WCF アプリケーションでは、依存関係の注入は Autofac IoC コンテナーによって提供されていました。 ASP.NET Core には依存関係の注入が組み込まれています。 クラスのメソッドにリポジトリを登録でき `ConfigureServices` `Startup` ます。

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Register the repository class as a scoped service (instance per request)
        services.AddScoped<IPortfolioRepository, PortfolioRepository>();

        services.AddGrpc();
    }

    // ...
}
```

実装は、 `IPortfolioRepository` 次のようにクラスのコンストラクターパラメーターとして指定できるようになりました `PortfolioService` 。

```csharp
public class PortfolioService : Protos.Portfolios.PortfoliosBase
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }
}
```

## <a name="implement-the-grpc-service"></a>GRPC サービスを実装する

これで、ファイルでメッセージとサービスを宣言したので `portfolios.proto` 、 `PortfolioService` grpc で生成されたクラスから継承するクラスにサービスメソッドを実装する必要があり `Portfolios.PortfoliosBase` ます。 メソッドは、基底クラスでとして宣言され `virtual` ます。 オーバーライドしないと、既定で gRPC "未実装" 状態コードが返されます。

まず、メソッドを実装し `Get` ます。 既定のオーバーライドは、次の例のようになります。

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

最初の問題は、 `request.TraderId` が文字列であり、サービスにが必要であることです `Guid` 。 文字列に対して予期される書式はですが、コードでは、 `UUID` 呼び出し元が無効な値を送信し、適切に応答する可能性を処理する必要があります。 サービスは、をスローし、標準のステータスコードを使用して問題を表すことで、エラーで応答でき `RpcException` `InvalidArgument` ます。

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    return base.Get(request, context);
}
```

に適切な値を指定した後 `Guid` `traderId` 、リポジトリを使用してポートフォリオを取得し、それをクライアントに返すことができます。

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a>内部モデルを gRPC メッセージにマップする

リポジトリが独自の POCO モデルを返すため、前のコードは実際には機能しません `Portfolio` が、gRPC には独自の Protobuf メッセージが必要です `Portfolio` 。 Entity Framework の種類をデータ転送の種類にマップする場合は、2つの間の変換を提供することをお勧めします。 この変換のためのコードを配置するための適切な場所は、Protobuf によって生成されるクラスにあります。これは、拡張できるようにクラスとして宣言されてい `partial` ます。

```csharp
namespace TraderSys.Portfolios.Protos
{
    public partial class PortfolioItem
    {
        public static PortfolioItem FromRepositoryModel(PortfolioData.Models.PortfolioItem source)
        {
            if (source is null) return null;

            return new PortfolioItem
            {
                Id = source.Id,
                ShareId = source.ShareId,
                Holding = source.Holding,
                CostCents = (int)(source.Cost * 100)
            };
        }
    }

    public partial class Portfolio
    {
        public static Portfolio FromRepositoryModel(PortfolioData.Models.Portfolio source)
        {
            if (source is null) return null;

            var target = new Portfolio
            {
                Id = source.Id,
                TraderId = source.TraderId.ToString(),
            };

            target.Items.AddRange(source.Items.Select(PortfolioItem.FromRepositoryModel));

            return target;
        }
    }
}
```

> [!NOTE]
> またはのような下位レベルの型変換を構成している限り、 [automapper](https://automapper.org/)のようなライブラリを使用して、内部モデルクラスから Protobuf 型への変換を処理することができ `string` / `Guid` `decimal` / `double` ます。

これで、変換コードが完成したので、メソッドの実装を完了でき `Get` ます。

```csharp
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}

```

メソッドの実装 `GetAll` も似ています。 `repeated`Protobuf メッセージのフィールドは型のプロパティとして生成される `readonly` `RepeatedField<T>` ため、 `AddRange` 次の例のようにメソッドを使用して、それらに項目を追加する必要があります。

```csharp
public override async Task<GetAllResponse> GetAll(GetAllRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolios = await _repository.GetAllAsync(traderId);

    var response = new GetAllResponse();
    response.Portfolios.AddRange(portfolios.Select(Portfolio.FromRepositoryModel));

    return response;
}
```

WCF 要求-応答サービスを gRPC に正常に移行したところで、ファイルからクライアントを作成する方法を見てみましょう `.proto` 。

## <a name="generate-client-code"></a>クライアントコードの生成

クライアントを格納するために、同じソリューションに .NET Standard クラスライブラリを作成します。 これは、主にクライアントコードを作成する例ですが、NuGet を使用してこのようなライブラリをパッケージ化し、他の .NET チームが使用できるように内部リポジトリに配布することもできます。 ソリューションにという名前の新しい .NET Standard クラスライブラリを追加 `TraderSys.Portfolios.Client` し、ファイルを削除し `Class1.cs` ます。

> [!CAUTION]
> [Grpc .Net クライアント](https://www.nuget.org/packages/Grpc.Net.Client)の NuGet パッケージには、.net Core 3.0 (または .NET Standard 2.1 に準拠した別のランタイム) が必要です。 以前のバージョンの .NET Framework と .NET Core は、 [Grpc. Core](https://www.nuget.org/packages/Grpc.Core) NuGet パッケージによってサポートされています。

Visual Studio 2019 では、以前のバージョンの Visual Studio で WCF プロジェクトにサービス参照を追加するのと同様の方法で、gRPC サービスへの参照を追加できます。 サービス参照と接続済みサービスはすべて同じ UI で管理されるようになりました。 UI にアクセスするには、ソリューションエクスプローラーでプロジェクトの [ **依存関係** ] ノードを右クリック `TraderSys.Portfolios.Client` し、[ **接続済みサービスの追加**] を選択します。 表示されたツールウィンドウで、[ **サービス参照** ] セクションを選択し、[ **新しい grpc サービス参照の追加**] を選択します。

![Visual Studio 2019 の接続済みサービス UI](media/migrate-request-reply/add-connected-service.png)

プロジェクト内のファイルを参照し `portfolios.proto` `TraderSys.Portfolios` 、[生成する **クラスの種類を選択**] の下にある [**クライアント**] をそのまま使用して、[ **OK]** を選択します。

![Visual Studio 2019 の [新しい gRPC サービス参照の追加] ダイアログボックス](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> このダイアログボックスには、[URL] フィールドも表示されることに注意してください。 組織がファイルの web アクセス可能なディレクトリを保持している場合は `.proto` 、この URL アドレスを設定するだけでクライアントを作成できます。

Visual Studio の [ **接続済みサービスの追加** ] 機能を使用すると、 `portfolios.proto` ファイルはコピーされるのではなく、リンクされた *ファイル* としてクラスライブラリプロジェクトに追加されるため、サービスプロジェクト内のファイルに対する変更は、クライアントプロジェクトで自動的に適用されます。 ファイル内の要素は次の `<Protobuf>` `csproj` ようになります。

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

> [!TIP]
> Visual Studio を使用していない場合、またはコマンドラインから作業する場合は、グローバルツールを使用して `dotnet-grpc` .Net gRPC プロジェクトの Protobuf 参照を管理できます。 詳細については、の[ `dotnet-grpc` ドキュメント](/aspnet/core/grpc/dotnet-grpc)を参照してください。

### <a name="use-the-portfolios-service-from-a-client-application"></a>クライアントアプリケーションからのポートフォリオサービスの使用

次のコードは、生成されたクライアントをコンソールアプリケーションで使用する方法の簡単な例です。 GRPC クライアントコードのより詳細な探索については、この章の最後にあります。

```csharp
public class Program
{
    public async Task Main(string[] args)
    {
        GetResponse response;

        using (var channel = GrpcChannel.ForAddress("https://localhost:5001"))
        {
            var client = new Protos.Portfolios.PortfoliosClient(channel);

            response = await client.GetAsync(new GetRequest
            {
                TraderId = args[0],
                PortfolioId = int.Parse(args[1])
            });
        }

        foreach (var item in response.Portfolio.Items)
        {
            Console.WriteLine($"Holding {item.Holding} of Share ID {item.ShareId}.");
        }
    }
}
```

これで、基本的な WCF アプリケーションを ASP.NET Core gRPC サービスに移行し、.NET アプリケーションからサービスを使用するクライアントを作成しました。 次のセクションでは、より複雑な双方向サービスについて説明します。

>[!div class="step-by-step"]
>[前へ](create-project.md)
>[次へ](migrate-duplex-services.md)
