---
title: クラウドの準備が整っている回復力のあるサービスを構築する。 クラウド内の一時的な障害を受け入れる
description: Azure Cloud と Windows コンテナーを使って既存の .NET アプリケーションを最新化する | クラウドに対応する回復力のあるサービスを構築する。 クラウド内の一時的な障害を受け入れる
ms.date: 12/21/2020
ms.openlocfilehash: 4d592a5761cdf696f3e57516d747cbd770512053
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025330"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>クラウドの準備が整っている回復力のあるサービスの構築:クラウド内の一時的な障害を受け入れる

回復性は、障害から回復し、引き続き機能する能力です。 回復性は障害を回避することではなく、障害が発生するという事実を受け入れ、ダウンタイムまたはデータの損失を回避するようにそれらに対応することです。 回復性の目的は、障害発生後にアプリケーションを完全に機能する状態に戻すことです。

少なくとも、ハードウェアベースのモデルではなく、ソフトウェアベースの回復性のモデルを実装する場合、アプリケーションはクラウドに対応できます。 クラウド アプリケーションは、確実に発生する部分的な障害を受け入れる必要があります。 アプリケーションを設計または部分的にリファクタリングし、予想される部分的な障害に対する回復力を実現します。 一時的なネットワークの停止、クラウド内のノードまたは VM のクラッシュなどの部分的な障害に対処するように設計する必要があります。 オーケストレーター クラスタ内でコンテナーを別のノードに移動するだけでも、アプリケーション内での断続的な短いエラーが発生する可能性があります。

## <a name="handling-partial-failure"></a>部分的なエラーの処理

クラウドベースのアプリケーションでは、部分的な障害のリスクが常にあります。 たとえば、1 つの Web サイト インスタンスまたはコンテナーに障害が発生する場合や、短時間使用不能になったり、応答しなくなったりする場合があります。 また、1 つの VM またはサーバーがクラッシュする可能性があります。

クライアントとサービスは別のプロセスなので、サービスがクライアントの要求に迅速に応答できないことがあります。 サービスが過負荷になり、要求への応答が遅くなる場合や、ネットワークの問題のために短時間アクセスできなくなる場合があります。

たとえば、Azure SQL Database のデータベースにアクセスするモノリシック .NET アプリケーションについて考えてみます。 Azure SQL Database またはその他のサードパーティ サービスが短時間応答しない場合 (Azure SQL Database が別のノードまたはサーバーに移動し、数秒間応答しない場合)、ユーザーが何らかのアクションを実行しようとしたとき、アプリケーションがクラッシュし、同時に例外が表示される場合があります。

HTTP サービスを使用するアプリでも、同様のシナリオが発生する場合があります。 短時間の一時的な障害の間に、ネットワークまたはサービス自体をクラウドで利用できない場合があります。

図 4-9 に示すような回復性があるアプリケーションでは、"エクスポネンシャル バックオフを伴う再試行" などの手法を実装して、リソースの一時的な障害を処理する機会をアプリケーションに与える必要があります。 また、アプリケーションには "サーキット ブレーカー" も使用することをお勧めします。 サーキット ブレーカーを使うと、実際には長期的な障害の場合に、アプリケーションによるリソースへのアクセスを防ぎます。 アプリケーションにサーキット ブレーカーを使用することで、アプリケーション自体へのサービス拒否攻撃の発生が回避されます。

![エクスポネンシャル バックオフによる再試行によって処理される部分的な障害の図。](./media/retry-partial-failures.png)

**図 4-9** エクスポネンシャル バックオフを使用した再試行によって処理される部分的な障害

これらの手法は、HTTP リソースとデータベース リソースの両方で使用できます。 図 4-9 では、アプリケーションは 3 層アーキテクチャに基づいているため、これらの手法はサービス レベル (HTTP) およびデータ層レベル (TCP) で必要です。 データベースに加えて 1 つのアプリ層のみを使用する (追加のサービスやマイクロサービスは使用しない) モノリシック アプリケーションでは、データベース接続レベルで一時的な障害を処理するだけで十分な場合があります。 このシナリオでは、データベース接続の特定の構成のみが必要です。

データベースにアクセスする回復性がある通信を実装する場合、使用している .NET のバージョンによっては簡単な可能性があります (たとえば、[Entity Framework 6 以降](/ef/ef6/fundamentals/connection-resiliency/retry-logic)。 これは、データベース接続を構成するだけの問題です)。 または、[一時的エラー処理アプリケーション ブロック](/previous-versions/msp-n-p/hh680934(v=pandp.50)) (以前のバージョンの .NET の場合) などの追加のライブラリを使用したり、独自のライブラリを実装したりする必要がある場合があります。

HTTP 再試行とサーキット ブレーカーを実装する場合、.NET の推奨事項は、.NET Standard 1.1 (カバレッジ: .NET Core 1.0、Mono、Xamarin、UWP、WP8.1 以降) と .NET Standard 2.0 以降 (カバレッジ: .NET Core 2.0 以降、.NET Core 3.0、および最近の Mono、Xamarin、UWP ターゲット) をターゲットとする、[Polly](https://github.com/App-vNext/Polly) ライブラリを使用することです。 nuget パッケージには、.NET Framework 4.6.1 と 4.7.2 の直接ターゲットも含まれています。

クラウドで部分的なエラーを処理する戦略を実装する方法については、次の参照情報を参照してください。

### <a name="additional-resources"></a>その他のリソース

- **部分的なエラーを処理するための回復性がある通信の実装**

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- **接続の回復性と再試行ロジックの Entity Framework (バージョン 6 以降)**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- **Transient Fault Handling Application Block**

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- **回復性の高い HTTP 通信のためのライブラリ**

    <https://github.com/App-vNext/Polly>

>[!div class="step-by-step"]
>[前へ](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[次へ](modernize-your-apps-with-monitoring-and-telemetry.md)
