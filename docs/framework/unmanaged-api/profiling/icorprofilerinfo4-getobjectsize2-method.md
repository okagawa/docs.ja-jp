---
description: '詳細について: ICorProfilerInfo4:: GetObjectSize2 メソッド'
title: ICorProfilerInfo4::GetObjectSize2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
ms.openlocfilehash: 986c3d99501e21feec95dd3b6014f8d11d809704
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794525"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a>ICorProfilerInfo4::GetObjectSize2 メソッド

指定したオブジェクトのサイズを返します。 で表現できる値よりも大きいオブジェクトのサイズをレポートすることによって、 [ICorProfilerInfo:: GetObjectSize](icorprofilerinfo-getobjectsize-method.md) メソッドを置き換え `ULONG` ます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a>パラメーター  

 `objectId`  
 からオブジェクトの ID です。  
  
 `pcSize`  
 入出力オブジェクトのサイズへのポインター (バイト単位)。  
  
## <a name="remarks"></a>解説  

 多くの場合、同じ種類の異なるオブジェクトのサイズは同じです。 ただし、配列や文字列など、一部の型では、オブジェクトごとにサイズが異なる場合があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo4 インターフェイス](icorprofilerinfo4-interface.md)
