---
title: IBindingDisplay::GetCurrentDisplay メソッド
ms.date: 03/30/2017
api_name:
- IBindingDisplay.GetCurrentDisplay
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type:
- apiref
ms.openlocfilehash: d52f089923d16f93345444c07ff8e0619644f2eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725156"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a>IBindingDisplay::GetCurrentDisplay メソッド

現在のバインディング表示情報を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `display`  
 [out, retval]バインディング表示情報を格納している safearray へのポインター。  
  
## <a name="remarks"></a>注釈  

 [IBindingDisplay:: InitializeForProcess](ibindingdisplay-initializeforprocess-method.md)メソッドが既に成功しており、プログラムがデバッガーによって停止されている必要があります。  
  
 呼び出し元は、SafeArrayDestroy を使用して、返されたメモリの割り当てを解除する必要があり `SAFEARRAY` ます。 [SafeArrayDestroy](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy)  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** BindingDisplay. h  
  
 **ライブラリ:** BindingDisplay .idl  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IBindingDisplay インターフェイス](ibindingdisplay-interface.md)
- [InitializeForProcess メソッド](ibindingdisplay-initializeforprocess-method.md)
