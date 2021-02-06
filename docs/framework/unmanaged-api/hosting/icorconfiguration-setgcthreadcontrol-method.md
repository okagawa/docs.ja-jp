---
description: '詳細について: ICorConfiguration:: SetGCThreadControl メソッド'
title: ICorConfiguration::SetGCThreadControl メソッド
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
ms.openlocfilehash: 8b9388bdefb9da2ce51b62ab68eeee54645e43ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636640"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a>ICorConfiguration::SetGCThreadControl メソッド

ガベージコレクションに対してブロックされる非ランタイムタスクのスレッドをスケジュールするためのコールバックインターフェイスを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pGCThreadControl`  
 から非ランタイムタスクのスレッドの中断をホストに通知する [Igcthreadcontrol](igcthreadcontrol-interface.md) オブジェクトへのポインター。  
  
## <a name="remarks"></a>解説  

 ホストは、スレッドを再スケジュールするかどうかにかかわらず、 [Igcthreadcontrol:: ThreadIsBlockingForSuspension](igcthreadcontrol-threadisblockingforsuspension-method.md) コールバック内で選択できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorConfiguration インターフェイス](icorconfiguration-interface.md)
