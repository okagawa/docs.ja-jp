---
description: '詳細について: IBindingDisplay:: InitializeForProcess メソッド'
title: IBindingDisplay::InitializeForProcess メソッド
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
ms.openlocfilehash: cf7f0f4d057659089bd7da173e5fac98a7c00dad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800410"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a>IBindingDisplay::InitializeForProcess メソッド

[IBindingDisplay](ibindingdisplay-interface.md)オブジェクトを初期化します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pid`  
 からプロセス識別子。  
  
## <a name="remarks"></a>解説  

 デバッガーは、 `InitializeForProcess` 作成時にメソッドを呼び出して、バインド表示を初期化します。 `InitializeForProcess` の他のメソッドが呼び出される前に、作成時にを呼び出す必要があり `IBindingDisplay` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** BindingDisplay. h  
  
 **ライブラリ:** BindingDisplay .idl  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IBindingDisplay インターフェイス](ibindingdisplay-interface.md)
