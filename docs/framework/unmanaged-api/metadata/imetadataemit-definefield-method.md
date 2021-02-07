---
description: '詳細について: IMetaDataEmit::D efineField メソッド'
title: IMetaDataEmit::DefineField メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
ms.openlocfilehash: 7636b1521de721cc183305e8a0763ff0a61f331b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753446"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField メソッド

指定したメタデータシグネチャを持つフィールドの定義を作成し、そのフィールド定義へのトークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineField (
    [in]  mdTypeDef   td,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwFieldFlags,
    [in]  PCCOR_SIGNATURE pvSigBlob,
    [in]  ULONG       cbSigBlob,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue,
    [out] mdFieldDef  *pmd
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `td`  
 から `mdTypeDef` 外側のクラスまたはインターフェイスのトークン。  
  
 `szName`  
 からUnicode でのフィールド名。  
  
 `dwFieldFlags`  
 からフィールド属性。 これは、値のビットマスクです `CorFieldAttr` 。  
  
 `pvSigBlob`  
 からBLOB としてのフィールドシグネチャ。  
  
 `cbSigBlob`  
 からのバイト数 `pvSigBlob` 。  
  
 `dwCPlusTypeFlag`  
 から`ELEMENT_TYPE_` *\** 定数値の。 これは `CorElementType` 値です。 フィールドの定数値を定義していない場合は、を使用し `ELEMENT_TYPE_END` ます。  
  
 `pValue`  
 からフィールドの定数値。  
  
 `cchValue`  
 からの (Unicode) 文字のサイズ `pValue` 。  
  
 `pmd`  
 入出力 `mdFieldDef` 割り当てられたトークン。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](imetadataemit2-interface.md)
