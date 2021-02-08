---
description: 詳細については、「SqlStreamChars. Seek (Int64, SeekOrigin) メソッド」を参照してください。
title: SqlStreamChars. Seek (Int64, SeekOrigin) メソッド (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 00f71aff95045d566b7932aec3f7e18259b4dfa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802568"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a>SqlStreamChars. Seek (Int64, SeekOrigin) メソッド

派生クラスでオーバーライドされた場合は、現在のストリーム内の位置を設定します。 このメソッドを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。 SQL Server での使用を目的としています。 他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a>パラメーター

`offset`\
`origin` からのバイト オフセット。

`origin`\
新しい位置を取得する参照ポイントを示す列挙値の1つ。

## <a name="returns"></a>戻り値

<xref:System.Int32>\
現在のストリーム内の新しい位置。

## <a name="remarks"></a>解説

> [!WARNING]
> `SqlStreamChars.Seek`メソッドはプライベートであり、コード内で直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.Data (System.Data.dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
