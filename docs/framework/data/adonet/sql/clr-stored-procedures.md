---
description: '詳細情報: CLR ストアド プロシージャ'
title: CLR ストアド プロシージャ
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: d136d3dcb12be2f87276a410c9fa0e713b7dfd52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723622"
---
# <a name="clr-stored-procedures"></a>CLR ストアド プロシージャ

ストアド プロシージャは、スカラー式では使用できないルーチンです。 ストアド プロシージャは、表形式の結果とメッセージをクライアントに返したり、データ定義言語 (DDL) ステートメントおよびデータ操作言語 (DML) ステートメントを呼び出したり、出力パラメーターを返したりすることができます。  
  
> [!NOTE]
> Microsoft Visual Basic では、出力パラメーターのサポートが Microsoft Visual C# と異なります。 パラメーターを参照によって渡す方式を指定し、次に示すように、\<Out()> 属性を適用して出力パラメーターを指定する必要があります。  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
詳細については、使用している SQL Server のバージョンに対応する [SQL Server ドキュメント](/sql)のバージョンを参照してください。
  
 **SQL Server のドキュメント**

1. [CLR ストアド プロシージャ](/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))  
  
## <a name="see-also"></a>関連項目

- [マネージ コードでの SQL Server 2005 オブジェクトの作成](/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))
- [ADO.NET の概要](../ado-net-overview.md)
