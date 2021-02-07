---
description: '詳細については、次を参照してください: いいね。'
title: ICorDebugController インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
ms.openlocfilehash: 588c41b5b8d87589facd6085655ed0ad415ec3aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710752"
---
# <a name="icordebugcontroller-interface"></a>ICorDebugController インターフェイス

コードの実行コンテキストを制御できる <xref:System.Diagnostics.Process> または <xref:System.AppDomain> のスコープを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|このメソッドは、互換性のために残されています。|  
|`ICorDebugController::CommitChanges`|このメソッドは、互換性のために残されています。|  
|[Continue メソッド](icordebugcontroller-continue-method.md)|次のように、 [コントロール](icordebugcontroller-stop-method.md)スレッドの実行を再開します。|  
|[Detach メソッド](icordebugcontroller-detach-method.md)|プロセスまたはアプリケーションドメインからデバッガーをデタッチします。|  
|[EnumerateThreads メソッド](icordebugcontroller-enumeratethreads-method.md)|プロセス内のアクティブなマネージスレッドの列挙子を取得します。|  
|[HasQueuedCallbacks メソッド](icordebugcontroller-hasqueuedcallbacks-method.md)|マネージコールバックが、指定されたスレッドに対して現在キューに登録されているかどうかを示す値を取得します。|  
|[IsRunning メソッド](icordebugcontroller-isrunning-method.md)|プロセス内のスレッドが現在実行中であるかどうかを示す値を取得します。|  
|[SetAllThreadsDebugState メソッド](icordebugcontroller-setallthreadsdebugstate-method.md)|プロセス内のすべてのマネージスレッドのデバッグ状態を設定します。|  
|[Stop メソッド](icordebugcontroller-stop-method.md)|プロセスでマネージコードを実行しているすべてのスレッドで協調停止を実行します。|  
|[Terminate メソッド](icordebugcontroller-terminate-method.md)|指定された終了コードを使用してプロセスを終了します。|  
  
## <a name="remarks"></a>解説  

 がプロセスを制御している場合、 `ICorDebugController` スコープにはプロセスのすべてのスレッドが含まれます。 `ICorDebugController`がアプリケーションドメインを制御している場合、スコープにはその特定のアプリケーションドメインのスレッドだけが含まれます。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
