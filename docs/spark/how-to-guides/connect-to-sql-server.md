---
title: .NET for Apache Spark を SQL Server に接続する
description: .NET for Apache Spark アプリケーションから SQL Server インスタンスに接続する方法について説明します。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 1fecd796aeefd6c5681c4c2ea623e89f3a5a3c1d
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439535"
---
# <a name="connect-net-for-apache-spark-to-sql-server"></a>.NET for Apache Spark を SQL Server に接続する

この記事では、[.NET for Apache Spark](https://github.com/dotnet/spark) アプリケーションから SQL Server インスタンスに接続する方法について説明します。

## <a name="configure-sql-server-to-grant-your-application-access"></a>アプリケーションへのアクセスを許可するように SQL Server を構成する

1. SQL Server 認証を選択して、ログイン ユーザーとパスワードを SQL Server インスタンスに追加します。
2. 次に示すように、該当するデータベース レベルでログイン ユーザーに必要な権限を付与します。

    ![SQL Server 権限](./media/connect-external-sources/SqlServerAuth.png)

3. SQL Server の既定のポート `1433` がファイアウォールを通過できることを確認します。
4. 次に示すように、SQL 構成マネージャーを開いて、ネットワーク構成で TCP/IP を有効にします。

    ![SQL Server TCP/IP の有効化](./media/connect-external-sources/SqlServerTCPIP.png)

    また、上の **[プロトコル]** タブの下にあるの **[すべて受信待ち]** の値にご注意ください。

5. `Listen All` が `No` に設定されている場合は、必要なすべての IP アドレスに対して TCP/IP ポートを 1433 に構成します。 それ以外の場合は、[IPAll] の [TCP ポート] を設定します。

    ![SQL Server TCP/IP ポート](./media/connect-external-sources/SQLServerTCPIIPPort.png)

## <a name="connect-to-sql-server-from-your-application"></a>アプリケーションから SQL Server に接続する

1. ご使用のアプリケーションを介してデータベース接続を提供するには、Microsoft JDBC Driver for SQL Server を使用します ([この公式 Web サイト](/sql/connect/jdbc/download-microsoft-jdbc-driver-for-sql-server?view=sql-server-ver15)からダウンロードしてください)。
2. ご使用のアプリケーションから SQL Server インスタンスとデータベースに接続するには、次の構成を設定します。
    1. **connection_url**: これは、SQL Server インスタンスまたはデータベースへの接続に使用される URL です。形式は次のとおりです。

        ```
        jdbc:sqlserver://<SQL_server_IP_address>:1433;instanceName=<instance_name>;databaseName=<database_name>;
        ```

    2. **dbtable**: アクセスされているテーブルの名前。
    3. **user**: SQL Server の構成の手順 1 で設定したログイン ユーザー。
    4. **password**: SQL Server の構成の手順 1 で設定したパスワード。
3. 次に示すように、上記の構成をご使用のアプリケーション コードで使用して、テーブルからデータを読み取ります。

    ```csharp
    static void Main()
    {
        SparkSession spark = SparkSession
            .Builder()
            .AppName("Connect to SQL Server")
            .GetOrCreate();

        string connection_url = "<URL to connect to SQL server instance>";
        string dbtable = "<database table to access>";
        string user = "<Login user name>";
        string password = "<Login user password>";

        DataFrame jdbcDF = spark.Read()
            .Format("jdbc")
            .Option("driver", "com.microsoft.sqlserver.jdbc.SQLServerDriver")
            .Option("url", connection_url)
            .Option("dbtable", dbtable)
            .Option("user", user)
            .Option("password", password).Load();
        jdbcDF.Show(); // Displays the content of the SQL table as a DataFrame
    }
    ```
