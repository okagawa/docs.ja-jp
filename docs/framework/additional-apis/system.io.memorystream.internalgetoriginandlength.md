---
description: '詳細については、次を参照してください: MemoryStream メソッド'
title: MemoryStream (System.IO) メソッド ()
ms.date: 11/19/2019
topic_type:
- apiref
api_name:
- System.IO.MemoryStream.InternalGetOriginAndLength
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 4232852c0835a43454f36271a43062e1240297a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802542"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a>MemoryStream.InternalGetOriginAndLength メソッド

メモリストリームの原点と長さの内部値を取得します。

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a>パラメーター

- `origin` <xref:System.Int32>\
  このメソッドから制御が戻るときに、新しいオブジェクトを作成するときに指定されたバイト配列のオフセット <xref:System.IO.MemoryStream> 。 バイト配列がによって作成された場合は0を格納 <xref:System.IO.MemoryStream> します。

- `length` <xref:System.Int32>\
  このメソッドから制御が戻るときに、メモリストリーム内のバイト数。

## <a name="remarks"></a>解説

> [!WARNING]
> `MemoryStream.InternalGetOriginAndLength`メソッドは内部であり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.IO>

**アセンブリ:** mscorlib.dll (mscorlib.dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
