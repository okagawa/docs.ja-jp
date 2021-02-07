---
description: '詳細情報: ICorProfilerInfo:: IsArrayClass メソッド'
title: ICorProfilerInfo::IsArrayClass メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
ms.openlocfilehash: 1eee0b834c63c3cfe15bd08776214ca8b2ba3f69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687234"
---
# <a name="icorprofilerinfoisarrayclass-method"></a>ICorProfilerInfo::IsArrayClass メソッド

指定したクラスが配列クラスであるかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a>パラメーター  

 `classId`  
 から調べるクラスの ID。  
  
 `pBaseElemType`  
 入出力配列要素の型を示す CorElementType 列挙値へのポインター。  
  
 `pBaseClassId`  
 入出力使用可能な場合は、配列要素のクラス ID へのポインター。  
  
 `pcRank`  
 入出力配列のランク (次元の数) を示す整数を指すポインターです。  
  
## <a name="remarks"></a>解説  

 指定したクラスが配列クラスの場合、 `IsArrayClass` メソッドは、null 以外の出力パラメーターの S_OK HRESULT と値を返します。 それ以外の場合は S_FALSE を返します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
