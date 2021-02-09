---
description: '詳細情報: ASP.NET アプリケーションでの SqlDependency'
title: ASP.NET アプリケーションでの SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: 686586af834884f97ff8e62fdc792b3cdc23f507
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767025"
---
# <a name="sqldependency-in-an-aspnet-application"></a>ASP.NET アプリケーションでの SqlDependency

ここでは、ASP.NET の <xref:System.Data.SqlClient.SqlDependency> オブジェクトを使用して、<xref:System.Web.Caching.SqlCacheDependency> を間接的に使用する方法の例を示します。 <xref:System.Web.Caching.SqlCacheDependency> オブジェクトでは <xref:System.Data.SqlClient.SqlDependency> を使用して通知をリッスンし、キャッシュを適切に更新します。  
  
> [!NOTE]
> このサンプル コードを実行するには、「[クエリ通知の有効化](enabling-query-notifications.md)」のスクリプトを実行してクエリ通知を有効にしておく必要があります。  
  
## <a name="about-the-sample-application"></a>サンプル アプリケーションについて  

 このサンプル アプリケーションでは、1 つの ASP.NET Web ページを使用して、SQL Server データベースである **AdventureWorks** に格納されている製品情報を <xref:System.Web.UI.WebControls.GridView> コントロールに表示します。 ページが読み込まれる際に、コードによって <xref:System.Web.UI.WebControls.Label> コントロールに現在の時刻が書き込まれます。 次に、<xref:System.Web.Caching.SqlCacheDependency> オブジェクトが定義され、最大 3 分間キャッシュ データが格納されるように <xref:System.Web.Caching.Cache> オブジェクトのプロパティが設定されます。 その後、データベースに接続され、データが取得されます。 ページが読み込まれ、アプリケーションが実行されると、ASP.NET によって、データがキャッシュから取得されます。これは、ページ上の時刻が変更されないことで確認できます。 監視しているデータが変化すると、ASP.NET によりキャッシュが無効化され、`GridView` コントロールに最新データが再入力されることで、`Label` コントロールに表示される時刻が更新されます。  
  
## <a name="creating-the-sample-application"></a>サンプル アプリケーションの作成  

 サンプル アプリケーションを作成して実行するには、次の手順に従います。  
  
1. 新しい ASP.NET Web サイトを作成します。  
  
2. <xref:System.Web.UI.WebControls.Label> および <xref:System.Web.UI.WebControls.GridView> コントロールを Default.aspx ページに追加します。  
  
3. ページのクラス モジュールを開き、次のディレクティブを追加します。  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. 次のコードをページの `Page_Load` イベントに追加します。  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5. `GetConnectionString` および `GetSQL` という 2 つのヘルパー メソッドを追加します。 定義される接続文字列は、統合セキュリティを利用します。 使用しているアカウントが、必要とされるデータベースへのアクセス許可を持っており、サンプル データベースの **AdventureWorks** で通知が有効になっていることを確認する必要があります。
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a>アプリケーションのテスト  

 このアプリケーションは Web フォームに表示されるデータをキャッシングし、操作が行われなければ 3 分ごとにデータを更新します。 データベースに変更があれば、キャッシュは直ちに更新されます。 Visual Studio からアプリケーションを実行すると、ブラウザーにページが読み込まれます。 表示されるキャッシュ更新時刻は、最後にキャッシュが更新された時刻を示します。 3 分間の待機後、ページを更新すると、ポストバック イベントが発生します。 ページに表示される時刻が変更されることに注意してください。 3 分経過する前にページを更新した場合、ページに表示される時刻は変わりません。  
  
 次に、Transact-SQL の UPDATE コマンドを使用して、データベースのデータを更新し、ページを更新します。 表示される時刻を見ると、データベースの新しいデータを使ってキャッシュが更新されたことがわかります。 キャッシュは更新されますが、ページに表示される時刻はポストバック イベントが発生するまで変更されないことに注意してください。  

## <a name="distributed-cache-synchronization-using-sql-dependency"></a>SQL の依存関係を使用した分散キャッシュの同期

[NCache](https://www.alachisoft.com/ncache) などの一部のサードパーティの分散キャッシュでは、[SQL の依存関係](https://www.alachisoft.com/resources/docs/ncache/prog-guide/sql-dependency.html)を使用した SQL データベースとキャッシュの同期がサポートされています。 詳細とソース コード実装の例については、[分散キャッシュの SQL の依存関係のサンプル](https://github.com/Alachisoft/NCache-Samples/tree/master/dotnet/Dependencies/SQLDependency)に関するページを参照してください。

## <a name="see-also"></a>関連項目

- [SQL Server のクエリ通知](query-notifications-in-sql-server.md)
- [ADO.NET の概要](../ado-net-overview.md)
