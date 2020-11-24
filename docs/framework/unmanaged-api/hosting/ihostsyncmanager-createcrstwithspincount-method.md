---
title: IHostSyncManager::CreateCrstWithSpinCount メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrstWithSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrstWithSpinCount
helpviewer_keywords:
- CreateCrstWithSpinCount method [.NET Framework hosting]
- IHostSyncManager::CreateCrstWithSpinCount method [.NET Framework hosting]
ms.assetid: 7280fa8c-3639-4abf-91cb-bc343da742d1
topic_type:
- apiref
ms.openlocfilehash: 6b2f57c7147cc8ff2abff848bd1e4661c2f5e728
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682884"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a>IHostSyncManager::CreateCrstWithSpinCount メソッド

同期のためにスピンカウントを持つクリティカルセクションオブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `dwSpinCount`  
 からクリティカルセクションオブジェクトのスピンカウントを指定します。  
  
 `ppCrst`  
 入出力 [IHostCrst](ihostcrst-interface.md) インスタンスのアドレスへのポインター。クリティカルセクションを作成できなかった場合は null。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`CreateCrstWithSpinCount` 正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。|  
|E_FAIL|原因不明の致命的なエラーが発生しました。 メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。 後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。|  
|E_OUTOFMEMORY|要求されたクリティカルセクションを作成するのに十分なメモリがありませんでした。|  
  
## <a name="remarks"></a>注釈  

 スピンカウントは、マルチプロセッサシステムでのみ使用されます。 スピンカウントは、使用できないクリティカルセクションに関連付けられているセマフォで待機操作を実行する前に、呼び出し元のスレッドがスピンする必要がある回数を指定します。 スピン操作中にクリティカルセクションが解放されると、呼び出し元のスレッドは待機操作を回避します。 `CreateCrstWithSpinCount` Win32 関数をミラー化 `InitializeCriticalSectionAndSpinCount` します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRSyncManager インターフェイス](iclrsyncmanager-interface.md)
- [IHostSemaphore インターフェイス](ihostsemaphore-interface.md)
- [IHostSyncManager インターフェイス](ihostsyncmanager-interface.md)
