---
description: '詳細について: IHostTaskManager:: ReverseLeaveRuntime メソッド'
title: IHostTaskManager::ReverseLeaveRuntime メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseLeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type:
- apiref
ms.openlocfilehash: 2fed157f6ea05243270b957cacdb00ba5a47a88f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680865"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a>IHostTaskManager::ReverseLeaveRuntime メソッド

コントロールが共通言語ランタイム (CLR) を離れていること、およびマネージコードから呼び出されたアンマネージ関数を入力していることをホストに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`ReverseLeaveRuntime` 正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。|  
|E_FAIL|原因不明の致命的なエラーが発生しました。 メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。 後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。|  
|E_OUTOFMEMORY|要求されたリソース割り当てを完了するために必要なメモリが不足しています。|  
  
## <a name="remarks"></a>解説  

 CLR はを呼び出して、 `ReverseLeaveRuntime` 現在実行中のタスクがアンマネージ関数に制御を返していることをホストに通知します。これは、プラットフォーム呼び出しによってマネージコードから呼び出されたものです。 への各呼び出し `ReverseLeaveRuntime` は、対応する [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md)への呼び出しと一致します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [CallNeedsHostHook メソッド](ihosttaskmanager-callneedshosthook-method.md)
- [EnterRuntime メソッド](ihosttaskmanager-enterruntime-method.md)
- [ICLRTask インターフェイス](iclrtask-interface.md)
- [ICLRTaskManager インターフェイス](iclrtaskmanager-interface.md)
- [IHostTask インターフェイス](ihosttask-interface.md)
- [IHostTaskManager インターフェイス](ihosttaskmanager-interface.md)
- [LeaveRuntime メソッド](ihosttaskmanager-leaveruntime-method.md)
- [プラットフォーム呼び出しの詳細](/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))
