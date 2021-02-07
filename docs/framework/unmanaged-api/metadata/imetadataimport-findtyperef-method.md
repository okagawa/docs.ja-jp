---
description: '詳細について: IMetaDataImport:: FindTypeRef メソッド'
title: IMetaDataImport::FindTypeRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
ms.openlocfilehash: 11e966256b5e75c1acff0bf1e6de0c96dc03e6aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745568"
---
# <a name="imetadataimportfindtyperef-method"></a>IMetaDataImport::FindTypeRef メソッド

指定したスコープ内にあり、指定した名前を持つ参照の TypeRef トークンへのポインターを取得し <xref:System.Type> ます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `tkResolutionScope`  
 から型参照が定義されているモジュール、アセンブリ、または型をそれぞれ指定する ModuleRef、AssemblyRef、または TypeRef トークン。  
  
 `szName`  
 から検索する型参照の名前。  
  
 `ptr`  
 入出力一致する TypeRef トークンへのポインター。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
