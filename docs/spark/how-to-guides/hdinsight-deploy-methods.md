---
title: .NET for Apache Spark ジョブを Azure HDInsight に送信する
description: spark-submit と Apache Livy を使用して、.NET for Apache Spark ジョブを Azure HDInsight に送信する方法について説明します。
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 74be4ecf33a9a881633da0630fa1c1a4bf0b19c6
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688164"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a>.NET for Apache Spark ジョブを Azure HDInsight に送信する

.NET for Apache Spark ジョブを HDInsight に展開するには、`spark-submit` と Apache Livy の 2 つの方法があります。

## <a name="deploy-using-spark-submit"></a>spark-submit を使用して展開する

[spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) コマンドを使用して、.NET for Apache Spark ジョブを Azure HDInsight に送信できます。

1. Azure portal の HDInsight Spark クラスターに移動し、 **[SSH およびクラスターのログイン]** を選択します。

2. ssh ログイン情報をコピーし、ログインをターミナルに貼り付けます。 クラスターの作成時に設定したパスワードを使用してクラスターにサインインします。 Ubuntu および Spark のウェルカム メッセージが表示されます。

3. **spark-submit** コマンドを使用して、HDInsight クラスターでアプリケーションを実行します。 このスクリプト例の **mycontainer** と **mystorageaccount** を、実際の BLOB コンテナーの名前とストレージ アカウントに置き換えることを忘れないでください。 また、microsoft-spark jar を、使用中の Spark および .NET for Apache Spark のバージョンに置き換えることを忘れないでください。

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a>Apache Livy を使用して展開する

[Apache Livy](https://livy.incubator.apache.org/) (Apache Spark REST API) を使用して、.NET for Apache Spark ジョブを Azure HDInsight Spark クラスターに送信することができます。 詳細については、[Apache Livy を使用したリモート ジョブ](/azure/hdinsight/spark/apache-spark-livy-rest-interface) に関するページを参照してください。

Linux では、`curl` を使用して次のコマンドを実行できます。

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a>次の手順

* [.NET for Apache Spark の概要](../tutorials/get-started.md)
* [.NET for Apache Spark アプリケーションを Azure HDInsight にデプロイする](../tutorials/hdinsight-deployment.md)
* [HDInsight のドキュメント](/azure/hdinsight/)
