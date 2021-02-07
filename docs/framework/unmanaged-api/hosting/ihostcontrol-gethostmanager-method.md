---
description: '詳細について: IHostControl:: GetHostManager メソッド'
title: IHostControl::GetHostManager メソッド
ms.date: 03/30/2017
api_name:
- IHostControl.GetHostManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::GetHostManager
helpviewer_keywords:
- GetHostManager method [.NET Framework hosting]
- IHostControl::GetHostManager method [.NET Framework hosting]
ms.assetid: 0fa34bca-ed18-4626-9e78-d33684d18edb
topic_type:
- apiref
ms.openlocfilehash: 7cc118808c8788504da2cc07a8c61c419d3c588f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708905"
---
# <a name="ihostcontrolgethostmanager-method"></a>IHostControl::GetHostManager メソッド

指定したを使用して、ホストのインターフェイスの実装へのインターフェイスポインターを取得し `IID` ます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `riid`  
 から `IID` 共通言語ランタイム (CLR) が照会しているインターフェイスの。  
  
 `ppObject`  
 入出力ホストに実装されたインターフェイスへのポインター。ホストがこのインターフェイスをサポートしていない場合は null。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`GetHostManager` 正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。|  
|E_FAIL|原因不明の致命的なエラーが発生しました。 メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。 後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。|  
|E_INVALIDARG|要求された `IID` が無効です。|  
|E_NOINTERFACE|要求されたインターフェイスはサポートされていません。|  
  
## <a name="remarks"></a>解説  

 CLR はホストに対してクエリを実行し、次のインターフェイスの1つまたは複数がサポートされているかどうかを判断します。  
  
- [IHostMemoryManager](ihostmemorymanager-interface.md)  
  
- [IHostTaskManager](ihosttaskmanager-interface.md)  
  
- [IHostThreadPoolManager](ihostthreadpoolmanager-interface.md)  
  
- [IHostIoCompletionManager](ihostiocompletionmanager-interface.md)  
  
- [IHostSyncManager](ihostsyncmanager-interface.md)  
  
- [IHostAssemblyManager](ihostassemblymanager-interface.md)  
  
- [IHostGCManager](ihostgcmanager-interface.md)  
  
- [IHostPolicyManager](ihostpolicymanager-interface.md)  
  
- [IHostSecurityManager](ihostsecuritymanager-interface.md)  
  
 ホストが指定されたインターフェイスをサポートしている場合は、そのインターフェイス `ppObject` の実装にを設定します。 それ以外の場合は、 `ppObject` を null に設定します。  
  
 ホストマネージャーをシャットダウンした場合でも、CLR はを呼び出しません `Release` 。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IHostControl インターフェイス](ihostcontrol-interface.md)
