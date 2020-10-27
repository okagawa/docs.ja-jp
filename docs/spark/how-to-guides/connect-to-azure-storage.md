---
title: ローカル コンピューターからリモート ストレージに接続する
description: ローカル コンピューターから .NET for Apache Spark を使用して Azure Storage アカウントに接続します。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dc0c3b44279756596f3d456616821e690710ae04
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224014"
---
# <a name="connect-to-azure-data-lake-storage-gen-2-or-wasb-account"></a>Azure Data Lake Storage Gen 2 または WASB アカウントに接続する

この記事では、Windows マシン上のローカルで実行されている [.NET for Apache Spark](https://github.com/dotnet/spark) のインスタンスを介して、Azure Data Lake Storage (ADLS) Gen 2 または Windows Azure Storage Blob (WASB) アカウントに接続する方法について説明します。

## <a name="set-up-the-environment"></a>環境を設定する

1. Hadoop を使用せずにビルドされた Apache Spark ディストリビューションを[公式 Web サイト](https://archive.apache.org/dist/spark/) ([.NET for Apache Spark でサポートされている](https://github.com/dotnet/spark#supported-apache-spark)バージョンを選択してください) からダウンロードし、ディレクトリに展開します。 このディレクトリに環境変数 `SPARK_HOME` を設定します。
2. [こちら](http://hadoop.apache.org/releases.html)から Apache Hadoop バイナリをダウンロードしてフォルダーに展開し、このフォルダーに `HADOOP_HOME` 環境変数を設定します。
3. [こちらの場所](https://github.com/cdarlint/winutils) (前の手順でインストールした Hadoop のバージョンに応じて異なります) から `winutils.exe` と `hadoop.dll` のファイルをダウンロードし、お使いの Hadoop の bin フォルダーに配置します。 すべての設定を正しく行うには、これらのバイナリが Windows 上に必要です (この詳細については、[こちらの Apache wiki](https://cwiki.apache.org/confluence/display/HADOOP2/WindowsProblems) を参照してください)。
4. `%HADOOP_HOME%\etc\hadoop\hadoop-env.cmd` ファイルに次の変更を加えて、Hadoop のインストールを構成します。
    1. DOS パスを使用して `JAVA_HOME` プロパティを設定します (Hadoop では `JAVA_HOME` 内のスペースが推奨されないため)。 これで次のようになります。`C:\Progra~1\Java\jdk1.8.0_241` (ローカル コンピューターにインストールされている任意のバージョンの Java を指します)。
    2. `%HADOOP_HOME%\share\hadoop\tools\lib\*` を `HADOOP_CLASSPATH` に追加します。
    最終的な `hadoop-env.cmd` ファイルは、次のようになります。

    ![最終的な hadoop-env.cmd ファイル](./media/connect-external-sources/hadoop-env.png)

## <a name="configure-your-storage-account-in-hadoop"></a>Hadoop でストレージ アカウントを構成する

1. [Azure portal](https://portal.azure.com) を介して接続する ADLS Gen 2 または WASB ストレージ アカウントを開き、 **[設定]** ブレードの下にある **[アクセス キー]** パネルを開き、key1 の **[キー]** の値をコピーします。
2. ここで、ADLS Gen2 アカウントにアクセスするように Hadoop を構成するには、クラスター全体の構成を含む `core-site.xml` (`%HADOOP_HOME%\etc\hadoop\` 内にあります) ファイルを編集する必要があります。 このファイルの `<configuration>` タグ内に次のプロパティを追加します。

    ```xml
    <configuration>
      <property>
        <name>fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.dfs.core.windows.net</name>
        <value>SharedKey</value>
        <description></description>
      </property>
      <property>
        <name>fs.azure.account.key.YOUR_ACCOUNT_NAME.dfs.core.windows.net</name>
        <value>YOUR ACCESS KEY (copied from Step 1)</value>
        <description>The secret password. Never share these.</description>
      </property>
    </configuration>
    ```

    WASB アカウントに接続しようとしている場合は、プロパティ名の `dfs` を `blob` に置き換えます。 たとえば、「 `fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.blob.core.windows.net` 」のように入力します。
3. `%HADOOP_HOME%` ディレクトリから次のコマンドを実行することで、Hadoop からストレージ アカウントへの接続をテストできます。

    ```bash
    bin\hdfs dfs -ls <URI to your account>
    ```

これにより、URI に指定されたパスにあるすべてのファイルおよびフォルダーの一覧が表示されます。

> [!NOTE]
> ストレージ アカウントに URI を派生させる形式は次のとおりです。
>
> ```
> For ADLS: abfs[s]://<file_system>@<account_name>.dfs.core.windows.net/<path>/<file_name>
> For WASB: wasb[s]://<file_system>@<account_name>.blob.core.windows.net/<path>/<file_name>
> ```

## <a name="connect-to-your-storage-account"></a>ストレージ アカウントに接続する

1. 上記のコマンドが動作した場合は、Spark を介してこのストレージ アカウントへのアクセスに進むことができます。 まず、`%HADOOP_HOME%` 内のコマンドラインからコマンド `hadoop classpath` を実行し、出力をコピーします。
2. 手順 1 で実行したコマンドの出力を環境変数 `SPARK_DIST_CLASSPATH` の値に設定します。
3. これで、次の簡単な例に示すように、abfs URI を使用して Spark .NET を介して ADLS または WASB ストレージ アカウントにアクセスできるようになります。 (この例では、すべての Apache Spark インストールに用意されている標準の [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) サンプル ファイルを使用します。):

    ```csharp
    SparkSession spark = SparkSession
       .Builder()
       .AppName("Connect to Azure Storage locally")
       .GetOrCreate();
    DataFrame df = spark.Read().Json("wasbs://file_system@account_name.blob.core.windows.net/path/people.json");
    //DataFrame df = spark.Read().Json("abfss://file_system@account_name.dfs.core.windows.net/path/file.json");
    df.Show();
    ```

    表示される結果は、次のように DataFrame (`df`) です。

    ```text
    +----+-------+
    | age|   name|
    +----+-------+
    |null|Michael|
    |  30|   Andy|
    |  19| Justin|
    +----+-------+
    ```
