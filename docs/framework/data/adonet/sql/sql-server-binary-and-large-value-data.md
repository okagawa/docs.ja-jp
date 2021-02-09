---
description: '詳細情報: SQL Server のバイナリ データと大きな値のデータ'
title: SQL Server のバイナリ データと大きな値のデータ
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 8c7da5d504af0bc1beeea7e210a6fff4157fb090
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767441"
---
# <a name="sql-server-binary-and-large-value-data"></a>SQL Server のバイナリ データと大きな値のデータ

SQL Server では `max` 指定子が提供されています。これにより、`varchar`、`nvarchar`、および `varbinary` データ型の記憶容量が拡張されています。 `varchar(max)`、`nvarchar(max)`、`varbinary(max)` は、総称して *大きな値のデータ型* と呼びます。 大きな値のデータ型を使用すると、最大で 2^31-1 バイトのデータを格納できます。  
  
 SQL Server 2008 では FILESTREAM 属性が導入されました。これはデータ型ではありませんが、列に定義できる属性であり、これを使用すると大きな値のデータをデータベースではなくファイル システムに格納できます。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [ADO.NET での大きい値 (max) データの変更](modifying-large-value-max-data.md)  
 大きな値のデータ型を扱う方法について説明します。  
  
 [FILESTREAM データ](filestream-data.md)  
 SQL Server 2008 で FILESTREAM 属性を使用して保存された大きな値のデータを扱う方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [SQL Server データ型と ADO.NET](sql-server-data-types.md)
- [ADO.NET における SQL Server データ操作](sql-server-data-operations.md)
- [ADO.NET でのデータの取得および変更](../retrieving-and-modifying-data.md)
- [ADO.NET の概要](../ado-net-overview.md)
