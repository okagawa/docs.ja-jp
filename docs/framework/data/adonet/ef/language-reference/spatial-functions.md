---
description: '詳細情報: 空間関数'
title: 空間関数
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: cde8f1b0fcf5904eb33fe061de69e566da2804dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767883"
---
# <a name="spatial-functions"></a>空間関数

空間型のリテラル形式はありません。 ただし、Well-Known Text 形式の文字列を使用して呼び出す正規の Entity Framework 関数を使用できます。 たとえば、次の関数呼び出しでは、ジオメトリ ポイントが作成されます。  
  
```sql  
GeometryFromText('POINT (43 -73)')  
```  
  
 <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> メソッドには、Entity Framework の空間に関するすべての正規のメソッドがあります。 目的のメソッドをクリックすると、関数に渡す必要のあるパラメーターを確認できます。
