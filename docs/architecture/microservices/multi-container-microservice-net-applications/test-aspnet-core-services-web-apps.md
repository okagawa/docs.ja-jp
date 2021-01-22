---
title: ASP.NET Core サービスと Web アプリのテスト
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | コンテナーで ASP.NET Core サービスと Web アプリをテストするためのアーキテクチャについて調べる。
ms.date: 01/13/2021
ms.openlocfilehash: dfd0a320491f92154bc9e2804d56c00120224e62
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188004"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>ASP.NET Core サービスと Web アプリのテスト

コントローラーは、すべての ASP.NET Core API サービスと ASP.NET MVC Web アプリケーションの中心になるものです。 そのため、アプリケーションが意図するとおりに動作するという信頼が必要です。 自動テストを行うと、この信頼が得られ、運用環境に提供する前にエラーを検出できます。

有効または無効な入力に基づくコントローラーの動作、および実行するビジネス操作の結果に基づくコントローラーの応答をテストする必要があります。 ただし、マイクロサービスに対してこれらの種類のテストを実行すべきです。

- 単体テスト。 これらのテストにより、アプリケーションの個々のコンポーネントが想定どおりに動作することが保証されます。 アサーションは、コンポーネント API をテストします。

- 統合テスト。 これらのテストにより、コンポーネント間の相互作用が、データベースなどの外部成果物に対して想定どおりに動作することが保証されます。 アサーションは、コンポーネント API や UI をテストしたり、データベース I/O やログ記録などの操作の副作用をテストしたりできます。

- 各マイクロサービスの機能テスト。 これらのテストにより、ユーザーの観点から、アプリケーションが想定どおりに動作することが保証されます。

- サービス テスト。 これらのテストでは、複数のサービスを同時にテストするなど、エンドツーエンド サービスのユース ケースが確実にテストされます。 この種類のテストでは、まず環境を準備する必要があります。 この場合、サービスを開始することを意味します (たとえば、docker-compose up を使用します)。

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>ASP.NET Core Web API の単体テストの実装

単体テストでは、アプリケーションの一部をインフラストラクチャや依存関係から切り離してテストします。 コントローラー ロジックの単体テストを行うときは、それが依存しているものやフレームワーク自体の動作ではなく、単一のアクションやメソッドの内容のみをテストします。 単体テストではコンポーネント間の相互作用の問題は検出しません。これは、統合テストの目的です。

コントローラーのアクションの単体テストでは、その動作にだけ注目するようにします。 コント ローラーの単体テストは、フィルター、ルーティング、モデル バインド (ViewModel または DTO への要求データのマッピング) などを回避できます。 1 つの事柄だけに注目してテストするため、一般に、単体テストは簡単に記述してすばやく実行できます。 適切に記述された一連の単体テストは、大きなオーバーヘッドなしに頻繁に実行できます。

単体テストは、xUnit.net、MSTest、Moq、NUnit などのテスト フレームワークに基づいて実装されます。 eShopOnContainers サンプル アプリケーションでは、xUnit を使用します。

Web API コントローラーの単体テストを記述する際には、C\# で new キーワードを直接使用してコントローラー クラスをインスタンス化することにより、できるだけ速くテストを実行します。 次の例では、[xUnit](https://xunit.net/) をテスト フレームワークとして使用し、これを行う方法を示します。

```csharp
[Fact]
public async Task Get_order_detail_success()
{
    //Arrange
    var fakeOrderId = "12";
    var fakeOrder = GetFakeOrder();

    //...

    //Act
    var orderController = new OrderController(
        _orderServiceMock.Object,
        _basketServiceMock.Object,
        _identityParserMock.Object);

    orderController.ControllerContext.HttpContext = _contextMock.Object;
    var actionResult = await orderController.Detail(fakeOrderId);

    //Assert
    var viewResult = Assert.IsType<ViewResult>(actionResult);
    Assert.IsAssignableFrom<Order>(viewResult.ViewData.Model);
}
```

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>各マイクロサービスの統合テストと機能テストの実装

前述のように、統合テストと機能テストにはさまざまな目的と目標があります。 しかし、ASP.NET Core コントローラーをテストするときにそれらのテストを実装する方法は似ているため、このセクションでは統合テストに注目します。

統合テストは、アプリケーションのコンポーネントが、組み立てたときに正しく動作することを確認します。 ASP.NET Core は、単体テスト フレームワークと組み込みのテスト Web ホストを使用した統合テストをサポートします。これは、ネットワークのオーバーヘッドなしで要求を処理するために使用できます。

単体テストとは異なり、統合テストにはしばしば、データベース、ファイル システム、ネットワーク リソース、Web 要求と応答などのアプリケーション インフラストラクチャの問題があります。 単体テストでは、これらの問題の代わりにフェイクやモック オブジェクトを使用します。 しかし、統合テストの目的は、対象のシステムがこれらの問題のシステムで期待どおりに動作することを確認することであるため、統合テストではフェイクやモック オブジェクトを使用しないでください。 代わりに、データベース アクセスや他のサービスからのサービス呼び出しなどのインフラストラクチャを含めます。

統合テストは、単体テストより大きなコード セグメントを実行し、インフラストラクチャ要素に依存するため、多くの場合、単体テストと比べて桁違いに低速になります。 そのため、記述して実行する統合テストの数を制限することをお勧めします。

ASP.NET Core には、ネットワークのオーバーヘッドなしで HTTP 要求を処理するために使用できる、組み込みのテスト Web ホストが含まれています。これは、実際の Web ホストの使用時よりもそれらのテストをより速く実行できるということです。 テスト Web ホスト (TestServer) は、Microsoft.AspNetCore.TestHost として NuGet コンポーネントでご利用いただけます。 これを統合テスト プロジェクトに追加して、ASP.NET Core アプリケーションをホストするために使用できます。

次のコードからわかるように、ASP.NET Core コントローラーの統合テストを作成すると、テスト ホストによってコントローラーがインスタンス化されます。 この機能は、HTTP 要求に相当しますが、より速く実行されます。

```csharp
public class PrimeWebDefaultRequestShould
{
    private readonly TestServer _server;
    private readonly HttpClient _client;

    public PrimeWebDefaultRequestShould()
    {
        // Arrange
        _server = new TestServer(new WebHostBuilder()
           .UseStartup<Startup>());
           _client = _server.CreateClient();
    }

    [Fact]
    public async Task ReturnHelloWorld()
    {
        // Act
        var response = await _client.GetAsync("/");
        response.EnsureSuccessStatusCode();
        var responseString = await response.Content.ReadAsStringAsync();
        // Assert
        Assert.Equal("Hello World!", responseString);
    }
}
```

#### <a name="additional-resources"></a>その他の技術情報

- **Steve Smith。コントローラーのテスト** (ASP.NET Core) \
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- **Steve Smith。統合テスト** (ASP.NET Core) \
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- **dotnet テストを使用した .NET での単体テスト** \
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- **xUnit.net**。 公式サイト。 \
    <https://xunit.net/>

- **単体テストの基本。** \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- **Moq**。 GitHub リポジトリ。 \
    <https://github.com/moq/moq>

- **NUnit**。 公式サイト。 \
    <https://nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a>マルチコンテナー アプリケーションでのサービス テストの実装

前述のとおり、マルチコンテナー アプリケーションをテストする際、すべてのマイクロサービスを Docker ホスト内やコンテナー クラスター内で実行している必要があります。 いくつかのマイクロサービスが関係する複数の操作を含むエンド ツー エンドのサービス テストでは、docker-compose up (または、オーケストレーターを使用している場合は相当するメカニズム) を実行して、Docker ホストでアプリケーション全体を展開して起動する必要があります。 アプリケーション全体とそのすべてのサービスが実行されると、エンド ツー エンドの統合テストと機能のテストを実行できます。

使用できる方法はいくつかあります。 アプリケーションの展開に使用する docker-compose.yml ファイルでは、ソリューション レベルで [dotnet test](../../../core/tools/dotnet-test.md) を使用してエントリ ポイントを拡張できます。 対象とするイメージで、テストを実行する別の Compose ファイルを使用することもできます。 コンテナー上のマイクロサービスとデータベースを含む統合テストで別の Compose ファイルを使用すれば、テストを実行する前に、関連するデータが元の状態に常にリセットされることを確認できます。

Compose アプリケーションが起動し実行されると、Visual Studio を実行している場合はブレークポイントと例外を活用できます。 または、Azure DevOps Services の CI パイプラインや Docker コンテナーをサポートする他の CI/CD システムで、統合テストを自動的に実行することができます。

## <a name="testing-in-eshoponcontainers"></a>eShopOnContainers でテストする

参照アプリケーション (eShopOnContainers) のテストが再構築され、次の 4 つのカテゴリができました。

1. **単体** テスト。 **{MicroserviceName}.UnitTests** プロジェクトに含まれている、従来の単純で定期的な単体テスト

2. **マイクロサービスの機能/統合テスト**。各マイクロサービスのインフラストラクチャに関するテスト ケースを含みます。他からは分離されていて、 **{MicroserviceName}.FunctionalTests** プロジェクトに含まれています。

3. **アプリケーションの機能/統合テスト**。マイクロサービスの統合に集中します。複数のマイクロサービスを実行するテスト ケースが含まれています。 これらのテストはプロジェクト **Application.FunctionalTests** にあります。

図 6-25 に示すように、単体テストと統合テストはマイクロサービス プロジェクト内のテスト フォルダーに編成されますが、アプリケーションとロード テストはルート フォルダー下で個別に管理されます。

![ソリューション内のテスト プロジェクトの一部を指している VS のスクリーンショット。](./media/test-aspnet-core-services-web-apps/eshoponcontainers-test-folder-structure.png)

**図 6-25**。 eShopOnContainers のテスト フォルダーの構造

マイクロサービスとアプリケーションの機能または統合テストは定期テスト ランナーを使用して Visual Studio から実行されますが、最初にソリューションの test フォルダーに含まれる一連の docker-compose ファイルを用いて必要なインフラストラクチャ サービスを開始する必要があります。

**docker-compose-test.yml**

```yml
version: '3.4'

services:
  redis.data:
    image: redis:alpine
  rabbitmq:
    image: rabbitmq:3-management-alpine
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
  nosqldata:
    image: mongo
```

**docker-compose-test.override.yml**

```yml
version: '3.4'

services:
  redis.data:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"
  sqldata:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosqldata:
    ports:
      - "27017:27017"
```

そのため、機能/統合テストを実行するには、最初にソリューションの test フォルダーから次のコマンドを実行する必要があります。

```console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

ご覧のように、これらの docker-compose ファイルでは Redis、RabbitMQ、SQL Server、および MongoDB のマイクロサービスのみが開始されます。

### <a name="additional-resources"></a>その他の技術情報

- eShopOnContainers の **ユニットと統合テスト** \
    <https://github.com/dotnet-architecture/eShopOnContainers/wiki/Unit-and-integration-testing>

- eShopOnContainers の **ロード テスト** \
    <https://github.com/dotnet-architecture/eShopOnContainers/wiki/Load-testing>

> [!div class="step-by-step"]
> [前へ](subscribe-events.md)
> [次へ](background-tasks-with-ihostedservice.md)
