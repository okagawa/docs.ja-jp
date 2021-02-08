---
description: '詳細について: ICorRuntimeHost:: GetConfiguration メソッド'
title: ICorRuntimeHost::GetConfiguration メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type:
- apiref
ms.openlocfilehash: d3e3f065c3957fb29daa11ed7c46858a53865c91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784835"
---
# <a name="icorruntimehostgetconfiguration-method"></a>ICorRuntimeHost::GetConfiguration メソッド

ホストが共通言語ランタイム (CLR) のコールバック構成を指定できるようにするオブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pConfiguration`  
 入出力CLR の構成に使用できる [ICorConfiguration](icorconfiguration-interface.md) オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 CLR は、初期化の前に構成する必要があります。それ以外の場合、 `GetConfiguration` メソッドはエラーを示す HRESULT を返します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** 1.0、1.1  
  
## <a name="see-also"></a>関連項目

- [ICorRuntimeHost インターフェイス](icorruntimehost-interface.md)
