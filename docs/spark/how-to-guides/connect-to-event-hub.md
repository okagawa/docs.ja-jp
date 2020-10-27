---
title: .NET for Apache Spark を Azure Event Hubs に接続する
description: ローカルの .NET for Apache Spark インスタンスから Azure Event Hub に接続する方法について説明します。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: c8fd10992e63674032af4148e0673a5330d9086c
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223966"
---
# <a name="connect-net-for-apache-spark-to-azure-event-hubs"></a>.NET for Apache Spark を Azure Event Hubs に接続する

この記事では、[.NET for Apache Spark](https://github.com/dotnet/spark) アプリケーションを Azure Event Hubs に接続して Apache Kafka ストリームの読み取りと書き込みを行う方法について説明します。

## <a name="prerequisites"></a>前提条件

イベント ハブについて Event Hubs 名前空間を準備します。 ステップ バイ ステップ ガイドについては、「[クイックスタート: Azure portal を使用してイベント ハブを作成する](/azure/event-hubs/event-hubs-create)」を参照してください。 イベント ハブの名前空間を作成するときは、必ず Standard 価格レベルを選択してください。

## <a name="what-is-azure-event-hubs"></a>Azure Event Hubs とは

[Azure Event Hubs](/azure/event-hubs/event-hubs-about) は、ビッグ データのストリーミング プラットフォームとなるイベント インジェスト サービスです。 これは、フル マネージドのサービスとしてのプラットフォーム (PaaS) であり、[Apache Kafka](https://kafka.apache.org/) と簡単に統合できます。これにより、独自のクラスターを管理、構成、または実行しなくても、PaaS Kafka エクスペリエンスが得られます。

## <a name="connect-your-application-to-azure-event-hubs"></a>アプリケーションを Azure Event Hubs に接続する

1. Event Hubs の接続文字列と完全修飾ドメイン名 (FQDN) を、後で使用するために取得します。 手順については、「[Get an Event Hubs connection string (Event Hubs の接続文字列を取得する)](/azure/event-hubs/event-hubs-get-connection-string)」を参照してください。
2. Kafka 用 Event Hubs からの読み取りを開始するには、コード内の名前空間の詳細を使用して次の構成を設定します。
    1. 次のように、アプリケーションで **BOOTSTRAP_SERVERS** と **EH_SASL** を更新します。

    ```csharp
    string BOOTSTRAP_SERVERS = "hostname:9093"; // 9093 is the port used to communicate with Event Hubs, see [troubleshooting guide](https://docs.microsoft.com/azure/event-hubs/troubleshooting-guide)
    string EH_SASL = "org.apache.kafka.common.security.plain.PlainLoginModule required username=\"$ConnectionString\" password=\"<CONNECTION_STRING>\";"; // Connection string obtained from Step 1
    ```

## <a name="read-from-azure-event-hub-stream"></a>Azure Event Hub ストリームから読み取る

これで、Kafka の場合と同様に Event Hubs でストリーミングを開始できるようになりました。 サンプル コードを次に示します。

```csharp
SparkSession spark = SparkSession
    .Builder()
    .AppName("Connect Event Hub")
    .GetOrCreate();

DataFrame df = spark
    .ReadStream()
    .Format("kafka")
    .Option("kafka.bootstrap.servers", BOOTSTRAP_SERVERS)
    .Option("subscribe", "spark-test")
    .Option("kafka.sasl.mechanism", "PLAIN")
    .Option("kafka.security.protocol", "SASL_SSL")
    .Option("kafka.sasl.jaas.config", EH_SASL)
    .Option("kafka.request.timeout.ms", "60000")
    .Option("kafka.session.timeout.ms", "60000")
    .Option("failOnDataLoss", "false")
    .Load();

DataFrame dfWrite = df
    .WriteStream()
    .OutputMode("append")
    .Format("console")
    .Start();
```

## <a name="write-to-azure-event-hub-stream"></a>Azure Event Hub ストリームに書き込む

次に示すように、同じ方法で Event Hubs に書き込むこともできます。

```csharp
// df is the DataFrame to write

df.WriteStream()
    .Format("kafka")
    .Option("topic", topics)
    .Option("kafka.bootstrap.servers", BOOTSTRAP_SERVERS)
    .Option("kafka.sasl.mechanism", "PLAIN")
    .Option("kafka.security.protocol", "SASL_SSL")
    .Option("kafka.sasl.jaas.config", EH_SASL)
    .Option("checkpointLocation", "./checkpoint")
    .Start();
```

## <a name="run-your-application"></a>アプリケーションを実行する

.NET for Apache Spark アプリケーションを実行するには、sbt プロジェクトの `build.sbt` で `libraryDependency` を使用して、Spark プロジェクトのビルド定義の一環として `spark-sql-kafka-0-10` モジュールを定義します。 `spark-submit` (または `spark-shell`) などの Spark 環境では、次のように `--packages` コマンドライン オプションを使用します。

```bash
spark-shell --packages org.apache.spark:spark-sql-kafka-0-10_2.12:2.4.5
```

> [!NOTE]
> 実行する Spark のバージョンに合わせて、パッケージのバージョンを必ず含めてください。
