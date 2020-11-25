---
title: ICorProfilerInfo::GetEventMask メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type:
- apiref
ms.openlocfilehash: 16bd8b09d5118171e669e9c428fb444384b5867d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722570"
---
# <a name="icorprofilerinfogeteventmask-method"></a>ICorProfilerInfo::GetEventMask メソッド

現在のイベント カテゴリを取得します。プロファイラーは、これに関するイベント通知を共通言語ランタイム (CLR) から受け取ります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pdwEvents`  
 [out] イベントのカテゴリを指定する 4 バイト値へのポインター。 各ビットは、異なる性能、動作、またはイベントの型を制御します。 ビットは、 [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) 列挙体に記述されています。  
  
## <a name="remarks"></a>注釈  
  
> [!NOTE]
> このメソッドではなく、 [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) メソッドを呼び出す必要があります。 メソッドは `SetEventMask` 引き続きサポートされますが、 [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) には追加機能が用意されています。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetEventMask2 メソッド](icorprofilerinfo5-geteventmask2-method.md)
- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
