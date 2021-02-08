---
description: '詳細については、次を参照してください: IHostSyncManager:: SetCLRSyncManager メソッド'
title: IHostSyncManager::SetCLRSyncManager メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.SetCLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type:
- apiref
ms.openlocfilehash: e2a6a54334f7b8a63696ead918f4f34e0c36e438
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784715"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a>IHostSyncManager::SetCLRSyncManager メソッド

現在の[IHostSyncManager](ihostsyncmanager-interface.md)インスタンスに関連付ける[ICLRSyncManager](iclrsyncmanager-interface.md)インスタンスを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pManager`  
 から `ICLRSyncManager` 共通言語ランタイム (CLR) によって提供されるインスタンスへのポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`SetCLRSyncManager` 正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。|  
|E_FAIL|原因不明の致命的なエラーが発生しました。 メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。 後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>解説  

 ホストと CLR の間の通信を容易にするために、ホストインターフェイスは通常、ペアになっています。 ペアの1つのメンバーはホストによって実装され、もう一方のメンバーは CLR によって実装されます。 ホスト側の実装として、 `IHostSyncManager` インターフェイスは、 `ICLRSyncManager` CLR によって実装されるインターフェイスに対応します。 CLR は、を呼び出して、 `SetCLRSyncManager` `ICLRSyncManager` 現在のインスタンスに関連付けられているホストのインスタンスを指定 `IHostSyncManager` します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRSyncManager インターフェイス](iclrsyncmanager-interface.md)
- [IHostSyncManager インターフェイス](ihostsyncmanager-interface.md)
