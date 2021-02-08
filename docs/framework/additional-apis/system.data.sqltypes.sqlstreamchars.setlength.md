---
description: 詳細については、「SqlStreamChars (Int64) メソッド」を参照してください。
title: SqlStreamChars. SetLength (Int64) メソッド (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.SetLength
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: d10ce55126ae09062fe895c3a686ce5d94174554
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804141"
---
# <a name="sqlstreamcharssetlengthint64-method"></a>SetLength (Int64) メソッド

派生クラスでオーバーライドされると、ストリームによって使用されるリソースを解放します。 このメソッドを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。 SQL Server での使用を目的としています。 他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a>パラメーター

`value`\
現在のストリームの希望の長さ (バイト数)。

## <a name="remarks"></a>解説

> [!WARNING]
> `SqlStreamChars.SetLength`メソッドはプライベートであり、コード内で直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.Data (System.Data.dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
