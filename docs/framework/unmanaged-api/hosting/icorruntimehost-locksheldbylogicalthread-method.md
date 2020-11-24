---
title: ICorRuntimeHost::LocksHeldByLogicalThread メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.LocksHeldByLogicalThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread
helpviewer_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread method [.NET Framework hosting]
- LocksHeldByLogicalThread method [.NET Framework hosting]
ms.assetid: c3601255-d894-4d7c-b1df-c31334551700
topic_type:
- apiref
ms.openlocfilehash: 16f34d91861f9fcae51691ab13549bdf1ef333a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671500"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a>ICorRuntimeHost::LocksHeldByLogicalThread メソッド

現在のスレッドが保持しているロックの数を取得します。  
  
 このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pCount`  
 入出力現在のスレッドが保持しているロックの数へのポインター。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** 1.0、1.1  
  
## <a name="see-also"></a>関連項目

- [ICorRuntimeHost インターフェイス](icorruntimehost-interface.md)
