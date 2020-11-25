---
title: IGCHost2::SetGCStartupLimitsEx メソッド
ms.date: 03/30/2017
api_name:
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
ms.openlocfilehash: 4dca62903a123765ceb8bb251b79455ad0e4730a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726809"
---
# <a name="igchost2setgcstartuplimitsex-method"></a>IGCHost2::SetGCStartupLimitsEx メソッド

ジェネレーション0のセグメントサイズと最大サイズを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `SegmentSize`  
 からガベージコレクションシステムによって使用されるセグメントのサイズ。  
  
 `MaxGen0Size`  
 からジェネレーション0の最大サイズ。  
  
## <a name="remarks"></a>注釈  

 を設定する値は、 `SetGCStartupLimitsEx` ホストを開始する前にのみ指定できます。 これらの値は後で変更することはできません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** GCHost、GCHost  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IGCHost2 インターフェイス](igchost2-interface.md)
