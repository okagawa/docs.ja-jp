---
description: '詳細情報: Oracle 分散トランザクション'
title: Oracle 分散トランザクション
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: d0c41920f18e0f56ebdf57e3cb82cf829a59c450
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786174"
---
# <a name="oracle-distributed-transactions"></a>Oracle 分散トランザクション

<xref:System.Data.OracleClient.OracleConnection> オブジェクトはトランザクションがアクティブであると判断した場合、既存の分散トランザクションに自動的に参加します。 自動トランザクション参加は、接続が開かれた場合または接続プールから取得された場合に行われます。 既存のトランザクションへの自動参加を無効にするには、  
  
```csharp  
Enlist=false  
```  
  
 を <xref:System.Data.OracleClient.OracleConnection> の接続文字列パラメーターとして指定します。  
  
## <a name="see-also"></a>関連項目

- [Oracle および ADO.NET](oracle-and-adonet.md)
- [ADO.NET の概要](ado-net-overview.md)
