---
description: '詳細について: ICorConfiguration:: Setg Stcontrol メソッド'
title: ICorConfiguration::SetGCHostControl メソッド
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type:
- apiref
ms.openlocfilehash: 4d3d6e5e5275adf02f9d693234a5c8e77714fd03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636651"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a>ICorConfiguration::SetGCHostControl メソッド

仮想メモリの制限を変更するようにホストに要求するために、ガベージコレクターによって使用されるコールバックインターフェイスを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pGCHostControl`  
 からガベージコレクターが仮想メモリの制限を変更するようにホストに要求できるようにする、 [igている Stcontrol](igchostcontrol-interface.md) オブジェクトへのポインター。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorConfiguration インターフェイス](icorconfiguration-interface.md)
