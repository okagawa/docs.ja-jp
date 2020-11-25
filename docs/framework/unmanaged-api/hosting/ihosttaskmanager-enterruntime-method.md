---
title: IHostTaskManager::EnterRuntime メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type:
- apiref
ms.openlocfilehash: 11515bbb5717222a0030c1953b4eab4eb1b83bb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731645"
---
# <a name="ihosttaskmanagerenterruntime-method"></a>IHostTaskManager::EnterRuntime メソッド

プラットフォーム呼び出しメソッドなどのアンマネージメソッドへの呼び出しが実行制御を共通言語ランタイム (CLR) に返すことをホストに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`EnterRuntime` 正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。|  
|E_FAIL|原因不明の致命的なエラーが発生しました。 メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。 後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。|  
|E_OUTOFMEMORY|要求された割り当てを完了するのに十分なメモリがありませんでした。|  
  
## <a name="remarks"></a>注釈  

 `EnterRuntime` が呼び出され、ホストに対して、以前のバージョンの [最小 Veruntime](ihosttaskmanager-leaveruntime-method.md) メソッドへの呼び出しが行われたこと、実行が終了したこと、およびランタイムに実行制御が返されたことをホストに通知します。  
  
> [!NOTE]
> [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md) は、以前の呼び出しが行われたアンマネージ関数 `LeaveRuntime` がマネージコードを呼び出していることをホストに通知するために呼び出されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [高度な COM 相互運用性](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [方法: PInvoke を使用してマネージコードからネイティブ Dll を呼び出す](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [ICLRTask インターフェイス](iclrtask-interface.md)
- [ICLRTaskManager インターフェイス](iclrtaskmanager-interface.md)
- [IHostTask インターフェイス](ihosttask-interface.md)
- [IHostTaskManager インターフェイス](ihosttaskmanager-interface.md)
- [LeaveRuntime メソッド](ihosttaskmanager-leaveruntime-method.md)
