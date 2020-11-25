---
title: IMethodMalloc::Alloc メソッド
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
ms.openlocfilehash: 58809f12e4dd4419b754caafc3f8b883b8bc5089
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721167"
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc メソッド

新しい Microsoft 中間言語 (MSIL) 関数本体に対して、指定された量のメモリを割り当てようとします。

## <a name="syntax"></a>構文

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a>パラメーター

`cb`\
からメソッド本体に割り当てるバイト数。

## <a name="remarks"></a>注釈

 割り当てられたメモリは、このアロケーターに関連付けられているモジュールのベースアドレスよりも大きいアドレスから開始されます。 つまり、各アロケーターは特定のモジュールに対して作成され、そのベースアドレスからの正のオフセットでメモリの割り当てが試行されます。 が、 `Alloc` モジュールのベースアドレスよりも大きいアドレスで要求されたバイト数を割り当てられなかった場合は、使用可能な実際のメモリ容量に関係なく E_OUTOFMEMORY を返します。

 メソッドは、 `Alloc` [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) メソッドと組み合わせて使用する必要があります。

## <a name="requirements"></a>要件

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

 **ヘッダー** : CorProf.idl、CorProf.h

 **ライブラリ:** CorGuids.lib

 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>関連項目

- [IMethodMalloc インターフェイス](imethodmalloc-interface.md)
