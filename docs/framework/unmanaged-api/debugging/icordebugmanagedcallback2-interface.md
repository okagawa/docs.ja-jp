---
title: ICorDebugManagedCallback2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
ms.openlocfilehash: 937a2fb322eb63461d90e215635e1b10ab6afd09
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689785"
---
# <a name="icordebugmanagedcallback2-interface"></a>ICorDebugManagedCallback2 インターフェイス

デバッガーの例外処理およびマネージド デバッグ アシスタント (MDA: Managed Debugging Assistants) をサポートするメソッドを提供します。 `ICorDebugManagedCallback2` は [、のように、の](icordebugmanagedcallback-interface.md) 論理上の拡張機能です。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ChangeConnection メソッド](icordebugmanagedcallback2-changeconnection-method.md)|指定した接続に関連付けられたタスクのセットが変更されたことをデバッガーに通知します。|  
|[CreateConnection メソッド](icordebugmanagedcallback2-createconnection-method.md)|新しい接続が作成されたことをデバッガーに通知します。|  
|[DestroyConnection メソッド](icordebugmanagedcallback2-destroyconnection-method.md)|指定された接続が終了したことをデバッガーに通知します。|  
|[Exception メソッド](icordebugmanagedcallback2-exception-method.md)|例外ハンドラーの検索が開始されたことをデバッガーに通知します。|  
|[ExceptionUnwind メソッド](icordebugmanagedcallback2-exceptionunwind-method.md)|例外アンワインド処理中の状態通知を提供します。|  
|[FunctionRemapComplete メソッド](icordebugmanagedcallback2-functionremapcomplete-method.md)|コードの実行が編集された関数の新しいバージョンに切り替わったことをデバッガーに通知します。|  
|[FunctionRemapOpportunity メソッド](icordebugmanagedcallback2-functionremapopportunity-method.md)|コードの実行が、編集された関数の古いバージョンのシーケンスポイントに達したことをデバッガーに通知します。|  
|[MDANotification メソッド](icordebugmanagedcallback2-mdanotification-method.md)|コード実行でマネージデバッグアシスタント (MDA) メッセージが検出されたことを通知します。|  
  
## <a name="remarks"></a>注釈  

 インターフェイスは、インターフェイスを拡張して、 `ICorDebugManagedCallback2` `ICorDebugManagedCallback` .NET Framework バージョン2.0 で導入された新しいデバッグイベントを処理します。  
  
 デバッガー `ICorDebugManagedCallback2` が .NET Framework 2.0 アプリケーションをデバッグしている場合は、を実装する必要があります。 またはのインスタンスは、 `ICorDebugManagedCallback` `ICorDebugManagedCallback2` コールバックオブジェクトとして [ICorDebug:: setmanagedhandler](icordebug-setmanagedhandler-method.md)に渡されます。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [マネージド デバッグ アシスタントによるエラーの診断](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)
