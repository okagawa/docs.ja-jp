---
title: SqlClient による LocalDB のサポート
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 55ab1346de6f5c14f15d01344a984c18edf30e02
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824481"
---
# <a name="sqlclient-support-for-localdb"></a>SqlClient による LocalDB のサポート

この記事では、LocalDB データベースに接続する方法について説明します。 LocalDB は SQL Server の軽量バージョンです。
  
## <a name="remarks"></a>Remarks
  
 LocalDB で実行できる操作の概要を次に示します。  
  
- sqllocaldb.exe または app.config ファイルを使用して LocalDB インスタンスを作成および開始する。  
  
- sqlcmd.exe を使用して LocalDB インスタンスにデータベースを追加および変更する。 たとえば、 `sqlcmd -S (localdb)\myinst`のようにします。  
  
- `AttachDBFilename` 接続文字列キーワードを使用して LocalDB インスタンスにデータベースを追加する。 `AttachDBFilename`を使用していて、 `Database` 接続文字列キーワードでデータベースの名前を指定しない場合、アプリケーションを閉じると、データベースは LocalDB インスタンスから削除されます。  
  
- 接続文字列に LocalDB インスタンスを指定する。 たとえば、インスタンス名が `myInstance`の場合、接続文字列には次の行が含まれます。  
  
    `server=(localdb)\\myInstance`  
  
 `User Instance=True` は LocalDB データベースに接続するときに使用することはできません。  
  
LocalDB のインストールの詳細については、「[SQL Server Express LocalDB](/sql/database-engine/configure-windows/sql-server-express-localdb)」を参照してください。
  
## <a name="programmatically-create-a-named-instance"></a>名前付きインスタンスをプログラムによって作成する  

 アプリケーションは、次のように名前付きインスタンスを作成してデータベースを指定できます。  
  
- app.config ファイルに作成するための LocalDB インスタンスを次のように指定する。  インスタンスのバージョン番号は LocalDB インストールのバージョン番号と同じである必要があります。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
- `server` 接続文字列キーワードを使用してインスタンス名を指定する。  `server` 接続文字列キーワードで指定されたインスタンス名は app.config ファイルで指定された名前と一致する必要があります。  
  
- .MDF ファイルを指定するには、 `AttachDBFilename` 接続文字列キーワードを使用する。  
  
## <a name="see-also"></a>関連項目

- [SQL Server の機能と ADO.NET](sql-server-features-and-adonet.md)
- [ADO.NET の概要](../ado-net-overview.md)
