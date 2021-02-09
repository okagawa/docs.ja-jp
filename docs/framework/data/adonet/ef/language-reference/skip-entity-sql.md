---
description: '詳細情報: SKIP (Entity SQL)'
title: SKIP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: f4924acae6e351e076b5795cf47d63966ebdcb43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768013"
---
# <a name="skip-entity-sql"></a>SKIP (Entity SQL)

物理的なページングは、ORDER BY 句の SKIP サブ句を使用して実行できます。 SKIP を ORDER BY 句と切り離して使用することはできません。

## <a name="syntax"></a>構文

```sql
[ SKIP n ]
```

## <a name="arguments"></a>引数

`n` \
スキップするアイテムの数。

## <a name="remarks"></a>Remarks

SKIP 式のサブ句が ORDER BY 句に存在する場合、結果は並べ替え順序に従って並べ替えられ、結果セットには SKIP 式の直後の行から始まる行が含まれます。 たとえば、SKIP 5 は、先頭の 5 行をスキップし、6 行目以降を返します。

> [!NOTE]
> TOP 修飾子と SKIP サブ句が同じクエリ式内に存在する場合、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリは無効です。 TOP 式を LIMIT 式に変更してクエリを記述し直す必要があります。

> [!NOTE]
> SQL Server 2000 では、キー以外の列で ORDER BY と共に SKIP を使用すると、不適切な結果が返される場合があります。 キー以外の列に重複するデータが存在する場合、指定された数を超える行はスキップされます。 これは、SQL Server 2000 での SKIP の変換方法によるものです。 たとえば、次のコードでは、 `E.NonKeyColumn` に重複値が存在する場合、5 行を超える行はスキップされます。
>
> ```sql
> SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L
> ```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のクエリ (「[クエリの結果をページングする方法](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))」で示されているもの) では、ORDER BY 演算子と SKIP を使用して、SELECT ステートメントで返されるオブジェクトで使用される並べ替え順序が指定されています。

## <a name="see-also"></a>関連項目

- [ORDER BY](order-by-entity-sql.md)
- [方法: クエリの結果をページングする](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [ページング](paging-entity-sql.md)
- [TOP](top-entity-sql.md)
