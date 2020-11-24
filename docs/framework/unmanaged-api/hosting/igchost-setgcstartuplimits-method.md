---
title: IGCHost::SetGCStartupLimits メソッド
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
ms.openlocfilehash: 0eea9dba57886edfef13c31948a9cff94c6c1bfd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687874"
---
# <a name="igchostsetgcstartuplimits-method"></a>IGCHost::SetGCStartupLimits メソッド

ジェネレーション0のセグメントサイズと最大サイズを設定します。  
  
> [!IMPORTANT]
> .NET Framework 4.5 以降では、 `DWORD` [IGCHost2:: SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) メソッドを使用して、セグメントサイズと最大ジェネレーション0のサイズをより大きい値に設定できます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `SegmentSize`  
 からガベージコレクションシステムによって使用されるセグメントのサイズ。  
  
 `MaxGen0Size`  
 からジェネレーション0の最大サイズ。  
  
## <a name="remarks"></a>注釈  

 `SetGCStartupLimits`メソッドを呼び出すことができるのは1回だけです。 これらの値は後で変更することはできません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** GCHost、GCHost  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IGCHost インターフェイス](igchost-interface.md)
