---
title: IAssemblyName::IsEqual メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
ms.openlocfilehash: 0fabf8159c2626d4e1716e3be60baaf1ec834032
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712977"
---
# <a name="iassemblynameisequal-method"></a>IAssemblyName::IsEqual メソッド

指定した[IAssemblyName](iassemblyname-interface.md) `IAssemblyName` 比較フラグに基づいて、指定した IAssemblyName オブジェクトがこのと等しいかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pName`  
 から `IAssemblyName` このと比較するオブジェクト `IAssemblyName` 。  
  
 `dwCmpFlags`  
 から比較に影響を与える [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) 値のビットごとの組み合わせ。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **.Net Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IAssemblyName インターフェイス](iassemblyname-interface.md)
- [fusion 列挙体](fusion-enumerations.md)
