---
description: '詳細について: IGCHost:: GetThreadStats メソッド'
title: IGCHost::GetThreadStats メソッド
ms.date: 03/30/2017
api_name:
- IGCHost.GetThreadStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type:
- apiref
ms.openlocfilehash: 2d923560e915a0c88035caad70ad91149d793cb8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709660"
---
# <a name="igchostgetthreadstats-method"></a>IGCHost::GetThreadStats メソッド

ガベージコレクションのスレッドごとの統計を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pFiberCookie`  
 から統計を取得するスレッドを指定するファイバークッキーへのポインター。  
  
 `pStats`  
 [入力、出力]指定したスレッドのガベージコレクションの統計情報を格納している [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) 構造体へのポインター。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** GCHost、GCHost  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IGCHost インターフェイス](igchost-interface.md)
