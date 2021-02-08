---
description: '詳細情報: IMetaDataImport:: FindField メソッド'
title: IMetaDataImport::FindField メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
ms.openlocfilehash: b8041a37b91f22722a05aec99c92c4f17c2b0610
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799305"
---
# <a name="imetadataimportfindfield-method"></a>IMetaDataImport::FindField メソッド

指定した <xref:System.Type> と指定した名前とメタデータシグネチャを持つフィールドの FieldDef トークンへのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `td`  
 から検索対象のフィールドを囲むクラスまたはインターフェイスの TypeDef トークン。 この値がの場合 `mdTokenNil` 、グローバル変数に対して参照が行われます。  
  
 `szName`  
 から検索するフィールドの名前。  
  
 `pvSigBlob`  
 からフィールドのバイナリメタデータシグネチャへのポインター。  
  
 `cbSigBlob`  
 からのサイズ (バイト単位) `pvSigBlob` 。  
  
 `pmb`  
 入出力一致する FieldDef トークンへのポインター。  
  
## <a name="remarks"></a>解説  

 フィールドは、外側のクラスまたはインターフェイス ( `td` )、その名前 ( `szName` )、および必要に応じてシグネチャ () を使用して指定し `pvSigBlob` ます。  
  
 署名は特定のスコープにバインドされるため、に渡されるシグネチャは、 `FindField` 現在のスコープで生成される必要があります。 署名には、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。 (トークンは、ローカルの TypeDef テーブルのインデックスです)。 現在のスコープのコンテキスト外でランタイムシグネチャを作成し、その署名をへの入力として使用することはできません `FindField` 。  
  
 `FindField` クラスまたはインターフェイスで直接定義されたフィールドのみを検索します。継承されたフィールドは見つかりません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
