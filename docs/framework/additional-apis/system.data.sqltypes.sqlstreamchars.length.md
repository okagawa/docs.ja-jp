---
description: '詳細情報: SqlStreamChars. Length プロパティ'
title: SqlStreamChars. Length プロパティ (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: b0a9686cadc6d4018c7f291f0326b71195fd5cf5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802594"
---
# <a name="sqlstreamcharslength-property"></a>SqlStreamChars. Length プロパティ

派生クラスでオーバーライドされた場合、現在のストリームの長さを取得します。 このプロパティを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。 SQL Server での使用を目的としています。 他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。

## <a name="syntax"></a>構文

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a>プロパティ値

<xref:System.Int64>\
ストリーム長。

## <a name="remarks"></a>解説

> [!WARNING]
> `SqlStreamChars.Length`プロパティはプライベートであり、コード内で直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのプロパティの使用はサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.Data (System.Data.dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
