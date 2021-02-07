---
description: '詳細について: IAssemblyName:: SetProperty メソッド'
title: IAssemblyName::SetProperty メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.SetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type:
- apiref
ms.openlocfilehash: cab132c2cd8a0744a2a946a1d8b21f49012c6eac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760689"
---
# <a name="iassemblynamesetproperty-method"></a>IAssemblyName::SetProperty メソッド

指定したプロパティ識別子によって参照されるプロパティの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `PropertyId`  
 から値が設定されるプロパティの一意の識別子。  
  
 `pvProperty`  
 からによって参照されるプロパティを設定する値 `PropertyId` 。  
  
 `cbProperty`  
 からのサイズ (バイト単位) `pvProperty` 。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IAssemblyName インターフェイス](iassemblyname-interface.md)
