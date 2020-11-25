---
title: ICLRControl インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
ms.openlocfilehash: acf449014f5bf5683d5488f8ed2ead963676fe6b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728342"
---
# <a name="iclrcontrol-interface"></a>ICLRControl インターフェイス

共通言語ランタイム (CLR) に対してホストが参照を取得し、その側面を構成できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetCLRManager メソッド](iclrcontrol-getclrmanager-method.md)|ホストが CLR を構成するために使用できる任意のマネージャー型のインスタンスへのインターフェイスポインターを取得します。|  
|[SetAppDomainManagerType メソッド](iclrcontrol-setappdomainmanagertype-method.md)|から派生した型を、 <xref:System.AppDomainManager> アプリケーションドメインマネージャーの型として設定します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRAssemblyIdentityManager インターフェイス](iclrassemblyidentitymanager-interface.md)
- [ICLRDebugManager インターフェイス](iclrdebugmanager-interface.md)
- [ICLRGCManager インターフェイス](iclrgcmanager-interface.md)
- [ICLRHostBindingPolicyManager インターフェイス](iclrhostbindingpolicymanager-interface.md)
- [ICLRHostProtectionManager インターフェイス](iclrhostprotectionmanager-interface.md)
- [ICLROnEventManager インターフェイス](iclroneventmanager-interface.md)
- [ICLRPolicyManager インターフェイス](iclrpolicymanager-interface.md)
- [IHostControl インターフェイス](ihostcontrol-interface.md)
- [ホスト インターフェイス](hosting-interfaces.md)
