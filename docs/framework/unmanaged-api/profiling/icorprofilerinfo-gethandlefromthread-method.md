---
title: ICorProfilerInfo::GetHandleFromThread メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
ms.openlocfilehash: 94c2c6e01e4188f1fa13c3b6a9f638d4b79a502f
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678183"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a>ICorProfilerInfo::GetHandleFromThread メソッド

スレッドの ID を Win32 スレッドハンドルにマップします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a>パラメーター  

 `threadId`  
 から割り当てられるスレッド ID。  
  
 `phThread`  
 入出力Win32 スレッドハンドルへのポインター。  
  
## <a name="remarks"></a>解説  

 プロファイラーは、 `DuplicateHandle` 使用する前にハンドルで Win32 関数を呼び出す必要があります。  

 このメソッドから返されたハンドルはランタイムによって所有されており、プロファイラーはそれを閉じることはできません。
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
