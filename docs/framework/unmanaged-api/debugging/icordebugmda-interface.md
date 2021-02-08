---
description: '詳細については、次を参照してください: いいね。'
title: ICorDebugMDA インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
ms.openlocfilehash: 8e6e779c58d71b07edc9b63dff72aef728ebe050
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801125"
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA インターフェイス

マネージド デバッグ アシスタント (MDA) メッセージを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetDescription メソッド](icordebugmda-getdescription-method.md)|この MDA の説明を格納している文字列を取得します。|  
|[GetFlags メソッド](icordebugmda-getflags-method.md)|この MDA に関連付けられているフラグを取得します。|  
|[GetName メソッド](icordebugmda-getname-method.md)|この MDA の名前を格納している文字列を取得します。|  
|[GetOSThreadId メソッド](icordebugmda-getosthreadid-method.md)|この MDA が実行されているオペレーティングシステムのスレッド id を取得します。|  
|[GetXML メソッド](icordebugmda-getxml-method.md)|この MDA に関連付けられている XML の完全ストリームを取得します。|  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [マネージド デバッグ アシスタントによるエラーの診断](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
