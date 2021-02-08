---
description: '詳細情報: SmiOrderProperty プロパティ'
title: SmiOrderProperty プロパティ (Microsoft. SqlServer. Server)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- Microsoft.SqlServer.Server.SmiOrderProperty.Item
- Microsoft.SqlServer.Server.SmiOrderProperty.get_Item
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: fc2151d3f36a6746e80e2fd6d611a803b2c3162e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767987"
---
# <a name="smiorderpropertyitem-property"></a>SmiOrderProperty プロパティ

エンティティの列の順序を取得します。 このプロパティを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。 SQL Server での使用を目的としています。 他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。

## <a name="syntax"></a>構文

```csharp
internal SmiColumnOrder Item { get; }
```

## <a name="property-value"></a>プロパティ値

列の順序。

## <a name="remarks"></a>解説

> [!WARNING]
> `SmiOrderProperty.Item`プロパティは内部であり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのプロパティの使用はサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:Microsoft.SqlServer.Server>

**アセンブリ:** System.Data (System.Data.dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
