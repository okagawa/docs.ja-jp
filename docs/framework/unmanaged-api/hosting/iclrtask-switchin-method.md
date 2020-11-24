---
title: ICLRTask::SwitchIn メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchIn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type:
- apiref
ms.openlocfilehash: e98ae17d55c74d32844da96137c258d076ebc2db
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691059"
---
# <a name="iclrtaskswitchin-method"></a>ICLRTask::SwitchIn メソッド

現在の [ICLRTask](iclrtask-interface.md) インスタンスが表すタスクが操作可能な状態であることを、共通言語ランタイム (CLR) に通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `threadHandle`  
 から現在のインスタンスによって表されるタスクが実行されている物理スレッドへのハンドル `ICLRTask` 。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`SwitchIn` 正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。|  
|E_FAIL|原因不明の致命的なエラーが発生しました。 メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。 後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。|  
|HOST_E_INVALIDOPERATION|`SwitchIn` は、以前の [Switchout メソッド](iclrtask-switchout-method.md)の呼び出しなしで呼び出されました。|  
  
## <a name="remarks"></a>注釈  

 パラメーターは、 `threadHandle` 現在のインスタンスによって表されるタスク `ICLRTask` がスケジュールされているオペレーティングシステムスレッドへのハンドルを表します。 このスレッドで偽装が発生した場合は、タスクを切り替える前に [IHostSecurityManager:: RevertToSelf](ihostsecuritymanager-reverttoself-method.md) を呼び出す必要があります。  
  
> [!NOTE]
> を呼び出していないを呼び出すと、が `SwitchIn` `SwitchOut` HRESULT 値 HOST_E_INVALIDOPERATION で失敗します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRTask インターフェイス](iclrtask-interface.md)
- [ICLRTaskManager インターフェイス](iclrtaskmanager-interface.md)
- [IHostTask インターフェイス](ihosttask-interface.md)
- [IHostTaskManager インターフェイス](ihosttaskmanager-interface.md)
