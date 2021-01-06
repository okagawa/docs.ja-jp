---
title: アプリケーションパフォーマンス管理-WCF 開発者向け gRPC
description: ASP.NET Core gRPC アプリケーションのログ記録、メトリック、トレース。
ms.date: 12/15/2020
ms.openlocfilehash: 8a2a89e268e3b2dffdcc945ac71b2de85b4d4964
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938456"
---
# <a name="application-performance-management"></a>アプリケーション パフォーマンス管理

Kubernetes のような運用環境では、アプリケーションが最適に実行されるように監視することが重要です。 特にログとメトリックは重要です。 GRPC を含む ASP.NET Core には、ログメッセージとメトリックデータの生成と管理のための組み込みのサポートと、 *トレース* データが用意されています。

## <a name="the-difference-between-logging-and-metrics"></a>ログ記録とメトリックの違い

*ログ記録* は、システムで発生した事柄に関する詳細情報を記録するテキストメッセージに関係しています。 ログメッセージには、スタックトレースなどの例外データや、メッセージに関するコンテキストを提供する構造化データが含まれる場合があります。 ログ出力は、通常、検索可能なテキストストアに書き込まれます。

*メトリック* は、ダッシュボードでグラフやグラフを使用して集計および表示するように設計された数値データを指します。 ダッシュボードには、アプリケーションの全体的な正常性とパフォーマンスが表示されます。 メトリックデータを使用して、しきい値を超えたときに自動アラートをトリガーすることもできます。 メトリックデータの例をいくつか次に示します。

- 要求の処理にかかった時間。
- サービスのインスタンスによって処理される1秒あたりの要求の数。
- インスタンスで失敗した要求の数。

## <a name="logging-in-aspnet-core-grpc"></a>GRPC ASP.NET Core のログイン

ASP.NET Core には、ログを記録するための組み込みのサポートが用意されて[います。](https://www.nuget.org/packages/Microsoft.Extensions.Logging) このライブラリのコア部分は Web SDK に含まれているため、手動でインストールする必要はありません。 既定では、ログメッセージは、標準出力 ("コンソール") と、アタッチされている任意のデバッガーに書き込まれます。 永続的な外部データストアにログを書き込むには、オプションの [ログシンクパッケージ](/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0#third-party-logging-providers)のインポートが必要になることがあります。

ASP.NET Core gRPC フレームワークは、詳細な診断ログメッセージをこのログ記録フレームワークに書き込みます。これにより、アプリケーション独自のメッセージと共に処理および格納することができます。

### <a name="produce-log-messages"></a>ログメッセージの生成

ログの拡張機能は ASP.NET Core の依存関係の注入システムに自動的に登録されるため、gRPC サービスの種類で logger をコンストラクターパラメーターとして指定できます。

```csharp
public class StockData : Stocks.StocksBase
{
    private readonly ILogger<StockData> _logger;

    public StockData(ILogger<StockData> logger)
    {
        _logger = logger;
    }
}
```

要求や例外などの多くのログメッセージは、ASP.NET Core および gRPC フレームワークコンポーネントによって提供されます。 独自のログメッセージを追加して、下位レベルの問題ではなく、アプリケーションロジックに関する詳細とコンテキストを提供します。

ログメッセージと使用可能なログシンクおよびターゲットの記述の詳細については、「  [.Net Core でのログ記録」および「ASP.NET Core](/aspnet/core/fundamentals/logging/)」を参照してください。

## <a name="metrics-in-aspnet-core-grpc"></a>ASP.NET Core gRPC のメトリック

.NET Core ランタイムには、メトリックを生成および監視するための一連のコンポーネントが用意されています。 これには、クラスやクラスなどの Api が含ま <xref:System.Diagnostics.Tracing.EventSource> <xref:System.Diagnostics.Tracing.EventCounter> れます。 これらの Api は、 [dotnet グローバルツール](../../core/diagnostics/dotnet-counters.md)や Windows イベントトレーシングなど、外部プロセスで使用できる基本的な数値データを生成できます。 独自のコードでを使用する方法の詳細につい `EventCounter` ては、「 [eventcounter の概要](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md)」を参照してください。

より高度なメトリックのほか、広範なデータストアにメトリックデータを書き込む場合は、 [アプリメトリック](https://www.app-metrics.io)と呼ばれるオープンソースプロジェクトを試すことができます。 この一連のライブラリには、コードをインストルメント化するための広範な種類のセットが用意されています。 また、Prometheus、InfluxDB、 [Application Insights](/azure/azure-monitor/app/app-insights-overview)などの時系列データベースを含むさまざまな種類のターゲットにメトリックを書き込むパッケージも提供します。 [AspNetCore](https://www.nuget.org/packages/App.Metrics.AspNetCore.Mvc/) NuGet パッケージでは、ASP.NET Core framework との統合によって自動的に生成される、基本的なメトリックの包括的なセットも追加されます。 プロジェクトの web サイトには、 [Grafana](https://grafana.com/) visualization platform でこれらのメトリックを表示するための[テンプレート](https://www.app-metrics.io/samples/grafana/)が用意されています。

### <a name="produce-metrics"></a>メトリックを生成する

ほとんどのメトリックプラットフォームでは、次の種類がサポートされています。

| メトリックの種類 | 説明 |
| ----------- | ----------- |
| カウンタ     | 要求やエラーなど、何かが発生する頻度を追跡します。 |
| ゲージ       | アクティブな接続など、時間の経過と共に変化する1つの値を記録します。 |
| ヒストグラム   | 任意の制限で値の分布を測定します。 たとえば、ヒストグラムは、データセットのサイズを追跡し、含まれている <10 レコード11-100、含まれているレコードの数、101-1000 レコードの数、および >1000 レコードの数をカウントできます。 |
| 測定       | さまざまな期間におけるイベントの発生率を測定します。 |
| Timer       | イベントの期間とその発生率を追跡し、ヒストグラムとして格納します。 |

*アプリメトリック* を使用すると、依存関係の注入によって `IMetrics` インターフェイスを取得し、grpc サービスのこれらのメトリックを記録するために使用できます。 次の例では、時間の経過と共に行われた要求の数をカウントする方法を示し `Get` ます。

```csharp
public class StockData : Stocks.StocksBase
{
    private static readonly CounterOptions GetRequestCounter = new CounterOptions
    {
        Name = "StockData_Get_Requests",
        MeasurementUnit = Unit.Calls
    };

    private readonly IStockRepository _repository;
    private readonly IMetrics _metrics;

    public StockData(IStockRepository repository, IMetrics metrics)
    {
        _repository = repository;
        _metrics = metrics;
    }

    public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
    {
        _metrics.Measure.Counter.Increment(GetRequestCounter);

        // Serve request...
    }
}
```

### <a name="store-and-visualize-metrics-data"></a>メトリックデータの格納と視覚化

メトリックデータを格納する最善の方法は、 *タイムシリーズデータベース* で、タイムスタンプでマークされた数値データ系列を記録するように設計された特殊なデータストアです。 これらのデータベースのうち最も一般的なものは、 [Prometheus](https://prometheus.io/) と [InfluxDB](https://www.influxdata.com/products/influxdb-overview/)です。 また Microsoft Azure は、 [Azure Monitor](/azure/azure-monitor/overview) サービスを介した専用のメトリックストレージも提供します。

メトリックデータを視覚化するための最新のソリューションは [Grafana](https://grafana.com)であり、幅広いストレージプロバイダーで動作します。 次の図は、StockData サンプルを実行している Linkerd service メッシュのメトリックを表示する Grafana ダッシュボードの例を示しています。

![Grafana ダッシュボードのスクリーンショット](media/application-performance-management/grafana-screenshot.png)

### <a name="metrics-based-alerting"></a>メトリックベースのアラート

メトリックデータの数値の性質は、警告システムを駆動し、定義された許容範囲外に値がある場合に開発者やサポートエンジニアに通知することが理想的であることを意味します。 既に説明したプラットフォームでは、電子メール、テキストメッセージ、ダッシュボード内視覚エフェクトなど、さまざまなオプションを使用したアラートのサポートが提供されています。

## <a name="distributed-tracing"></a>分散トレース

分散トレースは、監視の比較的最近の開発で、マイクロサービスと分散アーキテクチャの使用量が増加してきました。 クライアントのブラウザー、アプリケーション、またはデバイスからの単一の要求は、多くの手順とサブ要求に分割でき、ネットワーク全体で多くのサービスを使用します。 このアクティビティを使用すると、ログメッセージとメトリックを、トリガーされた特定の要求と関連付けるのが困難になります。 分散トレースは、要求に識別子を適用し、ログとメトリックを特定の操作に関連付けることができるようにします。 このトレースは、 [WCF のエンドツーエンドのトレース](../../framework/wcf/diagnostics/tracing/end-to-end-tracing.md)に似ていますが、複数のプラットフォームに適用されます。

分散トレースは急速に成長しており、標準化が開始されています。 クラウドネイティブコンピューティングファンデーションは、 [Jaeger](https://www.jaegertracing.io/)や[エラスティック APM](https://www.elastic.co/products/apm)などのバックエンドを操作するために、ベンダー中立のライブラリを提供しようとして、[オープントレース標準](https://opentracing.io)を作成しました。 同時に、Google は同じ問題のセットを解決するために [OpenCensus プロジェクト](https://opencensus.io/) を作成しました。 これら2つのプロジェクトは、新しいプロジェクトである [OpenTelemetry](https://opentelemetry.io)にマージされます。これは、将来の業界標準です。

### <a name="how-distributed-tracing-works"></a>分散トレースのしくみ

分散トレースは、 *範囲* の概念に基づいています。これは、1つの *トレース* の一部である名前付きの時間指定操作で、システムの複数のノードでの処理が必要になる場合があります。 新しい操作が開始されると、一意の識別子を使用してトレースが作成されます。 各サブ操作に対して、スパンは独自の識別子とトレース識別子を使用して作成されます。 要求がシステムを通過すると、さまざまなコンポーネントが *親* の識別子を含む *子* スパンを作成できます。 スパンには、トレース識別子とスパン識別子を含む *コンテキスト* と、キーと値のペア ( *荷物* と呼ばれます) の形式の有用なデータが含まれています。

### <a name="distributed-tracing-with-diagnosticsource"></a>分散トレース `DiagnosticSource`

.NET には、分散トレースおよびスパン ( [DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#diagnosticsource-users-guide)) に適切にマップされる内部モジュールがあります。 また、プロセス内で診断を生成して使用する簡単な方法が用意されているので、モジュールには `DiagnosticSource` *アクティビティ* の概念があります。 アクティビティは、実質的には、分散トレースまたはトレース内のスパンの実装です。 モジュールの内部では、識別子の割り当てなど、親/子アクティビティが処理されます。 型の使用方法の詳細については `Activity` 、 [GitHub のアクティビティユーザーガイド](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-user-guide)を参照してください。

`DiagnosticSource`はコアフレームワーク以降の一部であるため、いくつかのコアコンポーネントでサポートされています。 これには <xref:System.Net.Http.HttpClient> 、gRPC フレームワークでの明示的なサポートを含む、、Entity Framework Core、ASP.NET Core が含まれます。 ASP.NET Core が要求を受信すると、 [W3C トレースコンテキスト](https://www.w3.org/TR/trace-context) 標準に一致する HTTP ヘッダーのペアが確認されます。 ヘッダーが見つかった場合は、ヘッダーの id 値とコンテキストを使用してアクティビティが開始されます。 ヘッダーが見つからない場合は、標準形式に一致する生成された id 値を使用してアクティビティが開始されます。 このアクティビティの有効期間中に、フレームワークまたはアプリケーションコードによって生成される診断には、トレース id とスパン識別子をタグ付けできます。 サポートは、 `HttpClient` この機能をさらに拡張するために、すべての要求の現在のアクティビティを確認し、トレースヘッダーを送信要求に自動的に追加します。

ASP.NET Core gRPC クライアントおよびサーバーライブラリには、およびの明示的なサポートが含まれて `DiagnosticSource` `Activity` います。また、アクティビティを作成し、ヘッダー情報を自動的に適用して使用します。

> [!NOTE]
> これは、リスナーが診断情報を消費している場合にのみ発生します。 リスナーが存在しない場合、診断は書き込まれず、アクティビティも作成されません。

### <a name="add-your-own-diagnosticsource-and-activity"></a>独自の `DiagnosticSource` およびを追加する `Activity`

独自の診断を追加したり、アプリケーションコード内に明示的な範囲を作成したりするには、『 [DiagnosticSource User guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#instrumenting-with-diagnosticsourcediagnosticlistener) And [Activity user guide 』](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-usage)を参照してください。

### <a name="store-distributed-trace-data"></a>分散トレースデータを格納する

このドキュメントの執筆時点では、OpenTelemetry プロジェクトは依然として初期段階にあり、.NET アプリケーションではアルファ品質のパッケージのみを使用できます。 OpenTracing プロジェクトには、現在、より成熟したライブラリが用意されています。

OpenTracing API については、次のセクションで説明します。 代わりに、アプリケーションで OpenTelemetry API を使用する場合は、GitHub の [OpenTelemetry .NET SDK リポジトリ](https://github.com/open-telemetry/opentelemetry-dotnet) を参照してください。

#### <a name="use-the-opentracing-package-to-store-distributed-trace-data"></a>OpenTracing パッケージを使用して分散トレースデータを格納する

[Opentracing NuGet パッケージ](https://www.nuget.org/packages/OpenTracing/)は、opentracing に準拠しているすべてのバックエンド (とは独立して使用でき `DiagnosticSource` ます) をサポートしています。 OpenTracing API の投稿プロジェクト ( [Opentracing](https://www.nuget.org/packages/OpenTracing.Contrib.NetCore/)) には、追加のパッケージがあります。 このパッケージは、リスナーを追加し、 `DiagnosticSource` イベントとアクティビティをバックエンドに自動的に書き込みます。 このパッケージを有効にすることは、NuGet からインストールし、クラスにサービスとして追加するのと同じように簡単です `Startup` 。

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddOpenTracing();
    }
}
```

OpenTracing パッケージは抽象レイヤーであるため、バックエンドに固有の実装が必要です。 OpenTracing API の実装は、次のオープンソースバックエンドで使用できます。

| 名前 | Package | Web サイト |
| ---- | ------- | -------- |
| Jaeger | [Jaeger](https://www.nuget.org/packages/Jaeger/) | [jaegertracing.io](https://jaegertracing.io) |
| エラスティック APM | [エラスティック. NetCoreAll](https://www.nuget.org/packages/Elastic.Apm.NetCoreAll/) | [elastic.co/products/apm](https://www.elastic.co/products/apm) |

.NET 用 OpenTracing API の詳細については、GitHub の opentracing [for C#](https://github.com/opentracing/opentracing-csharp) と [opentracing Contrib c#/.NET Core](https://github.com/opentracing-contrib/csharp-netcore) リポジトリを参照してください。

>[!div class="step-by-step"]
>[前へ](load-balancing.md)
>[次へ](appendix.md)
