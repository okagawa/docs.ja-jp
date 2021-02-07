---
description: '詳細について: ICorProfilerInfo:: GetThreadInfo メソッド'
title: ICorProfilerInfo::GetThreadInfo メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type:
- apiref
ms.openlocfilehash: 5514b1c4860067a07bf922e9d9a8bfab8c05e218
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760551"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a>ICorProfilerInfo::GetThreadInfo メソッド

指定したスレッドの現在の Win32 スレッド id を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a>パラメーター  

 `threadId`  
 から現在の Win32 ID を取得するスレッドの ID。  
  
 `pdwWin32ThreadId`  
 入出力指定したスレッドの現在の Win32 スレッド ID へのポインター。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
