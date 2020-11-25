---
title: IMetaDataEmit::DefineTypeDef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
ms.openlocfilehash: 2e75b6322e40fe010e9e0a3412a99c0d3460afae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719360"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef メソッド

共通言語ランタイム型の型定義を作成し、その型定義のメタデータトークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `szTypeDef`  
 からUnicode での型の名前。  
  
 `dwTypeDefFlags`  
 [入力] `TypeDef` アトリビュート. これは、値のビットマスクです `CoreTypeAttr` 。  
  
 `tkExtends`  
 から基本クラスのトークン。 またはトークンのいずれかである必要があり `mdTypeDef` `mdTypeRef` ます。  
  
 `rtkImplements`  
 からこのクラスまたはインターフェイスが実装するインターフェイスを指定するトークンの配列。  
  
 `ptd`  
 入出力 `mdTypeDef` 割り当てられたトークン。  
  
## <a name="remarks"></a>注釈  

 のフラグは、 `dwTypeDefFlags` 作成される型が共通型システム参照型 (クラスまたはインターフェイス) であるか、共通型システム値型であるかを指定します。  
  
 このメソッドは、指定されたパラメーターに応じて、 `mdInterfaceImpl` この型によって継承または実装される各インターフェイスのレコードを作成することもできます。 ただし、このメソッドはこれらのトークンを返しません `mdInterfaceImpl` 。 クライアントが後でトークンを追加または変更する場合は、 `mdInterfaceImpl` インターフェイスを使用してトークンを列挙する必要があり `IMetaDataImport` ます。 インターフェイスの COM セマンティクスを使用する場合は `[default]` 、既定のインターフェイスをの最初の要素として指定する必要があり `rtkImplements` ます。クラスに設定されたカスタム属性は、クラスに既定のインターフェイスがあることを示します (これは常に、クラスに対して宣言されている最初のトークンと見なされ `mdInterfaceImpl` ます)。  
  
 配列の各要素 `rtkImplements` `mdTypeDef` は、または `mdTypeRef` トークンを保持します。 配列の最後の要素は、である必要があり `mdTokenNil` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](imetadataemit2-interface.md)
