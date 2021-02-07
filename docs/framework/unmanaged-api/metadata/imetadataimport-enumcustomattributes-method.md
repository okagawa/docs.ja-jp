---
description: '詳細について: IMetaDataImport:: EnumCustomAttributes メソッド'
title: IMetaDataImport::EnumCustomAttributes メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 1c55ea4b72483e5dc30425172b95be7f77e8a62a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677588"
---
# <a name="imetadataimportenumcustomattributes-method"></a>IMetaDataImport::EnumCustomAttributes メソッド

指定した型またはメンバーに関連付けられているカスタム属性定義トークンを列挙します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `phEnum`  
 [入力、出力]返された列挙子へのポインター。  
  
 `tk`  
 から列挙体のスコープのトークン、またはすべてのカスタム属性の0。  
  
 `tkType`  
 から列挙する属性の型のコンストラクター、またはすべての型のコンストラクターのトークン `null` 。  
  
 `rCustomAttributes`  
 入出力カスタム属性トークンの配列。  
  
 `cMax`  
 [in] `rCustomAttributes` 配列の最大サイズ。  
  
 `pcCustomAttributes`  
 [out、省略可能]で返されるトークン値の実際の数 `rCustomAttributes` 。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumCustomAttributes` 正常に返されました。|  
|`S_FALSE`|列挙するカスタム属性はありません。 この場合、 `pcCustomAttributes` は0になります。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
