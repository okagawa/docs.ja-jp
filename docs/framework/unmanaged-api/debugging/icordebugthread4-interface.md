---
description: 詳細については、「ICorDebugThread4 インターフェイス」を参照してください。
title: ICorDebugThread4 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
ms.openlocfilehash: 4ad587cee81ce635df0a8917b7a6d68e60aaf0b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800917"
---
# <a name="icordebugthread4-interface"></a>ICorDebugThread4 インターフェイス

スレッドのブロック情報を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetBlockingObjects メソッド](icordebugthread4-getblockingobjects-method.md)|スレッドブロック情報を提供する [CorDebugBlockingObject](cordebugblockingobject-structure.md) 構造体の順序付けられた列挙体を提供します。|  
|[HadUnhandledException メソッド](icordebugthread4-hadunhandledexception-method.md)|スレッドで未処理の例外が発生したかどうかを示します。|  
|[GetCurrentCustomDebuggerNotification メソッド](icordebugthread4-getcurrentcustomdebuggernotification-method.md)|現在のスレッドの現在の [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) オブジェクトを取得します。|  
  
## <a name="remarks"></a>解説  

 このインターフェイスは、ICorDebugThread2、 [ICorDebugThread3](icordebugthread3-interface.md) の各インターフェイスの論理的な拡張機能です。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
