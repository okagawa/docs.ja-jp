---
description: 詳細については、次を参照してください。 SqlStreamChars. 読み取り (Char [], Int32, Int32) メソッド
title: SqlStreamChars. Read (Char [], Int32, Int32) メソッド (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: a899ddff7b7242fcc32aaf7b7f7794970596027b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802581"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a>SqlStreamChars. Read (Char [], Int32, Int32) メソッド

派生クラスでオーバーライドされると、入力ストリームから次の文字セットを読み取ります。 このメソッドを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。 SQL Server での使用を目的としています。 他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>パラメーター

`buffer`\
読み取る文字配列。

`offset`\
Origin を基準とするオフセット。

`count`\
現在のストリームから読み取る文字数。

## <a name="returns"></a>戻り値

<xref:System.Int32>\
バッファーに読み取られた合計文字数。

## <a name="remarks"></a>解説

> [!WARNING]
> `SqlStreamChars.Read`メソッドはプライベートであり、コード内で直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.Data (System.Data.dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
