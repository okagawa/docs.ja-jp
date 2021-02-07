---
description: '詳細については、次の情報を参照してください:: EnumerateThreads メソッド'
title: ICorDebugController::EnumerateThreads メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
ms.openlocfilehash: b53425de36be5a435ef0dac538c5165f41db63f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710778"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a>ICorDebugController::EnumerateThreads メソッド

プロセス内のアクティブなマネージスレッドの列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppThreads`  
 入出力プロセス内でアクティブになっているすべてのマネージスレッドの列挙子を表す "いい Threadenum" オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 スレッドがアクティブであると見なされるのは、"CreateThread" コールバックがディスパッチされてから、" [](icordebugmanagedcallback-createthread-method.md) [Managedcallback:: exitthread](icordebugmanagedcallback-exitthread-method.md) " コールバックがディスパッチされる前です。 マネージスレッドは、必ずしもスタック上にマネージフレームを持つとは限りません。 スレッドは、によっては、"、 [" という](icordebugmanagedcallback-createprocess-method.md) ように列挙できます。 列挙体は、自然に空になります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
