---
description: 詳細については、「SqlStreamChars. CanSeek プロパティ」を参照してください。
title: SqlStreamChars. CanSeek プロパティ (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 5919a66bef9ac31e0ef15ad4af64b456700605f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802620"
---
# <a name="sqlstreamcharscanseek-property"></a>SqlStreamChars. CanSeek プロパティ

派生クラスでオーバーライドされた場合、現在のストリームがシーク操作をサポートしているかどうかを示す値を取得します。 このプロパティを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。 SQL Server での使用を目的としています。 他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a>プロパティ値

<xref:System.Boolean>\
`true` 現在のストリームがシーク操作をサポートしている場合は。それ以外の場合は `false` 。

## <a name="remarks"></a>解説

> [!WARNING]
> `SqlStreamChars.CanSeek`プロパティはプライベートであり、コード内で直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのプロパティの使用はサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.Data (System.Data.dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
