---
description: '詳細について: IMetaDataEmit::D efineTypeDef メソッド'
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
ms.openlocfilehash: ca0c74b8c067771e9f45a8c00639d75c9ad08de1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784042"
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
  
## <a name="remarks"></a>解説  

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
