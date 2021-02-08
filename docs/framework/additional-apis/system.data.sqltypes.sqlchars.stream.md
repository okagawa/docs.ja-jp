---
description: '詳細情報: SqlChars. Stream プロパティ'
title: SqlChars. Stream プロパティ (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlChars.Stream
- System.Data.SqlTypes.SqlChars.get_Stream
- System.Data.SqlTypes.SqlChars.set_Stream
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9af0df98b268a749d890ab1b40dddbbe98ced8d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802646"
---
# <a name="sqlcharsstream-property"></a>SqlChars.Stream プロパティ

文字ストリームを取得または設定します。 このプロパティを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。 SQL Server での使用を目的としています。 他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。

```csharp
internal SqlStreamChars Stream { get; set; }
```

## <a name="property-value"></a>プロパティ値

`System.Data.SqlTypes.SqlStreamChars`\
文字ストリーム。

## <a name="remarks"></a>解説

> [!WARNING]
> `SqlChars.Stream`プロパティは内部であり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのプロパティの使用はサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.Data (System.Data.dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
