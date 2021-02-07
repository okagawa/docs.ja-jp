---
description: '詳細について: IMetaDataEmit:: SetTypeDefProps メソッド'
title: IMetaDataEmit::SetTypeDefProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
ms.openlocfilehash: 1160d20e7ceb422390f8cd725a75fdb4f42318e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706501"
---
# <a name="imetadataemitsettypedefprops-method"></a>IMetaDataEmit::SetTypeDefProps メソッド

[IMetaDataEmit::D efineTypeDef](imetadataemit-definetypedef-method.md)の前の呼び出しで定義された型の機能を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `td`  
 から `mdTypeDef` [IMetaDataEmit::D efineTypeDef](imetadataemit-definetypedef-method.md)の元の呼び出しから取得されたトークン。  
  
 `dwTypeDefFlags`  
 [入力] `TypeDef` アトリビュート. これは、値のビットマスクです `CorTypeAttr` 。  
  
 `tkExtends`  
 から `mdToken` 基本クラスの。 [IMetaDataEmit::D efineImportType](imetadataemit-defineimporttype-method.md)、またはの以前の呼び出しから取得さ `null` れます。  
  
 `rtkImplements[]`  
 からこの型が実装するインターフェイスのトークンの配列。 これらの `mdTypeRef` トークンは、 [IMetaDataEmit::D efineImportType](imetadataemit-defineimporttype-method.md)を使用して取得されます。 配列の最後の要素は、である必要があり `mdTokenNil` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](imetadataemit2-interface.md)
