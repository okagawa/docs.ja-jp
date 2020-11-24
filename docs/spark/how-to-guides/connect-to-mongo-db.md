---
title: .NET for Apache Spark を MongoDB に接続する
description: .NET for Apache Spark アプリケーションから MongoDB インスタンスに接続する方法について説明します。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 945e494e8a027d438bf4659d989da6033a13f6f0
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687604"
---
# <a name="connect-net-for-apache-spark-to-mongodb"></a>.NET for Apache Spark を MongoDB に接続する

この記事では、.NET for Apache Spark アプリケーションから MongoDB インスタンスに接続する方法について説明します。

## <a name="prerequisites"></a>前提条件

1. [データベースといくつかのコレクション](https://docs.mongodb.com/manual/core/databases-and-collections/)が追加された稼働中の MongoDB サーバー (ローカル サーバーの場合は[こちらのコミュニティ サーバー](https://www.mongodb.com/try/download/community)をダウンロードします。または、クラウド MongoDB サービスの場合は [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) を試すことができます)。

## <a name="set-up-your-mongodb-instance"></a>MongoDB インスタンスを設定する

.NET for Apache Spark が MongoDB インスタンスと通信できるようにするには、次の手順に従って、正しく設定されていることを確認する必要があります。

1. アプリケーションで接続に使用されるユーザー名とパスワードを作成し、mongo シェルをから次のコマンドを使用してユーザーに必要なアクセス許可とロールを付与します。

    ```bash
    use database
    db.createUser(
      {
        user: "mySparkUser",
        pwd: "<password>",
        roles: [ { role: "userAdminAnyDatabase", db: "admin" }, "readWriteAnyDatabase" ]
      }
    )
    ```

2. .NET for Apache Spark アプリケーションが実行されているマシンの IP アドレスが、MongoDB サーバーが接続できるようにホワイトリストに登録されていることを確認します。 その方法については、[こちらのガイド](https://docs.atlas.mongodb.com/security/add-ip-address-to-list/)を参照してください。

## <a name="configure-your-net-for-apache-spark-application"></a>.NET for Apache Spark アプリケーションを構成する

1. 次の変数を設定して、MongoDB インスタンスと通信し、コレクションから読み取るようにアプリケーションを構成します。
    1. **authURI**:"アプリケーションが必要な MongoDB インスタンスに接続することを承認する接続文字列"。 この形式は次のとおりです。

        ```
        "mongodb+srv://<username>:<password>@<cluster_address>/<database>.<collection>"
        ```

    2. **username**:前のセクションの手順 1 で作成したアカウントのユーザー名
    3. **password**:作成したユーザー アカウントのパスワード
    4. **cluster_address**: MongoDB クラスターのホスト名またはアドレス
    5. **database**:接続先の MongoDB データベース
    6. **collection**:読み取る MongoDB コレクション。 (この例では、すべての Apache Spark インストールに用意されている標準の [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) サンプル ファイルを使用します)。

2. 次の簡単なコード スニペットに示すように、`com.mongodb.spark.sql.DefaultSource` 形式は `spark.Read()` を使用します。

    ```csharp
    class Program
    {
        static void Main()
        {
            var authURI = "mongodb+srv://<username>:<password>@<cluster_address>/<database>.<collection>?retryWrites=true&w=majority";
            SparkSession spark = SparkSession
                .Builder()
                .AppName("Connect to Mongo DB example")
                .Config("spark.mongodb.input.uri", authURI)
                .GetOrCreate();

            DataFrame df = spark.Read().Format("com.mongodb.spark.sql.DefaultSource").Load();
            df.PrintSchema();
            df.Show();
            spark.Stop();
        }
    }
    ```

## <a name="run-your-application"></a>アプリケーションを実行する

.NET for Apache Spark アプリケーションを実行するには、sbt プロジェクトの `build.sbt` で `libraryDependency` を使用して、Spark プロジェクトのビルド定義の一環として `mongo-spark-connector` モジュールを定義します。 `spark-submit` (または `spark-shell`) などの Spark 環境では、次のように `--packages` コマンドライン オプションを使用します。

```bash
spark-submit --master local --packages org.mongodb.spark:mongo-spark-connector_2.12:3.0.0 --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar yourApp.exe
```

> [!NOTE]
> 実行する Spark のバージョンに合わせて、パッケージのバージョンを必ず含めてください。

表示される結果は、次のように DataFrame (`df`) です。

```text
+--------------------+----+-------+
|                 _id| age|   name|
+--------------------+----+-------+
|[5f7c28438029a134...|null|Michael|
|[5f7c287f8029a134...|  30|   Andy|
|[5f7c289a8029a134...|  19| Justin|
+--------------------+----+-------+
```
