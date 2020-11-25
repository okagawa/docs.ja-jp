---
title: CLRRuntimeHost コクラス
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
ms.openlocfilehash: 7c77cb2e89cb8fd87bf219780b9460649de19c9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731767"
---
# <a name="clrruntimehost-coclass"></a>CLRRuntimeHost コクラス

ランタイムによるコード実行を管理するためのインターフェイスを提供します。  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a>インターフェイス  
  
|インターフェイス|説明|  
|---------------|-----------------|  
|[ICLRRuntimeHost インターフェイス](iclrruntimehost-interface.md)|ランタイムによるアプリケーションの実行を制御するためのメソッドを提供します。|  
|[ICLRValidator インターフェイス](iclrvalidator-interface.md)|ポータブル実行可能イメージを検証し、検証エラーの詳細なレポートを作成するためのメソッドを提供します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト コクラス](hosting-coclasses.md)
