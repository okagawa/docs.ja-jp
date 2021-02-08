---
description: 詳細については、「SqlStreamChars. Write (Char [], Int32, Int32) メソッド」を参照してください。
title: SqlStreamChars. Write (Char [], Int32, Int32) メソッド (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 3031b57902215df01c5c30625281a99be73ba2d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802555"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a>SqlStreamChars. Write (Char [], Int32, Int32) メソッド

派生クラスでオーバーライドされた場合、現在のストリームに文字シーケンスを書き込み、書き込んだ文字数だけストリーム内の現在位置を進めます。 このメソッドを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。 SQL Server での使用を目的としています。 他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>パラメーター

`buffer`  
書き込む文字配列。

`offset`  
Origin を基準とするオフセット。

`count`  
現在のストリームに書き込む文字数。

## <a name="remarks"></a>解説

> [!WARNING]
> `SqlStreamChars.Write`メソッドはプライベートであり、コード内で直接使用するためのものではありません。
>
> Microsoft では、この方法を使用した運用アプリケーションの作成をサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.Data (System.Data.dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
