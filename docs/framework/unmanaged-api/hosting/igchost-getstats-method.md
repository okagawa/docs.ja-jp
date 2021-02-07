---
description: '詳細について: IGCHost:: GetStats メソッド'
title: IGCHost::GetStats メソッド
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
ms.openlocfilehash: 564224d01e23c8ac1fe81025ee87dabc41ed5166
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709692"
---
# <a name="igchostgetstats-method"></a>IGCHost::GetStats メソッド

ガベージコレクションシステムの現在の状態の統計を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pStats`  
 [入力、出力]ガベージコレクションシステムの現在の状態の統計情報を格納している [COR_GC_STATS](cor-gc-stats-structure.md) 構造体へのポインター。  
  
## <a name="remarks"></a>解説  

 統計は、ガベージコレクションシステムが動作するためにスマートアロケーションシステムによって使用される場合があります。 たとえば、割り当てシステムでは、統計情報を確認した後に、メモリを追加したり、コレクションを強制したりする必要があることを判断できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** GCHost、GCHost  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IGCHost インターフェイス](igchost-interface.md)
