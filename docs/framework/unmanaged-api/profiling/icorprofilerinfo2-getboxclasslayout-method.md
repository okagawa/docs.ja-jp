---
description: '詳細について: ICorProfilerInfo2:: GetBoxClassLayout メソッド'
title: ICorProfilerInfo2::GetBoxClassLayout メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetBoxClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type:
- apiref
ms.openlocfilehash: 0bc9ccc80da8bcc89cfe73eaa240310c01e6ca8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760509"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a>ICorProfilerInfo2::GetBoxClassLayout メソッド

指定された値型がボックス化されている場合の位置に関する情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a>パラメーター  

 `classId`  
 からボックス化された値の型を記述するクラスの ID。  
  
 `pBufferOffset`  
 入出力値型のボックス化されたオブジェクト ID ポインターを基準とするオフセットを表す整数。  
  
## <a name="remarks"></a>解説  

 `pBufferOffset`値は、ボックス内の値の型の場所です。 ボックス化されたオブジェクトにを適用した後 `pBufferOffset` 、値型のクラスレイアウトを使用して、オブジェクトの値を解釈できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 インターフェイス](icorprofilerinfo2-interface.md)
