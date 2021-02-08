---
description: 詳細については、「SqlStreamChars. IsNull プロパティ」を参照してください。
title: SqlStreamChars. IsNull プロパティ (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: b1408a8ba9cd1c38f73d5fa6b818f441d6223bc8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791921"
---
# <a name="sqlstreamcharsisnull-property"></a>SqlStreamChars. IsNull プロパティ

派生クラスでオーバーライドされた場合、ストリームがであるかどうかを示す値を取得し `null` ます。 このプロパティを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。 SQL Server での使用を目的としています。 他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。

## <a name="syntax"></a>構文

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a>プロパティ値

<xref:System.Boolean>\
`true` ストリームがの場合は `null` 。それ以外の場合は `false` 。

## <a name="remarks"></a>解説

> [!WARNING]
> `SqlStreamChars.IsNull`プロパティはプライベートであり、コード内で直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのプロパティの使用はサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.Data (System.Data.dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
