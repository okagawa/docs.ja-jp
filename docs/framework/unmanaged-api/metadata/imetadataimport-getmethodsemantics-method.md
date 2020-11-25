---
title: IMetaDataImport::GetMethodSemantics メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type:
- apiref
ms.openlocfilehash: cc01a417c3246ad2554c506f21e37a3cbbdeb991
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733188"
---
# <a name="imetadataimportgetmethodsemantics-method"></a>IMetaDataImport::GetMethodSemantics メソッド

指定した MethodDef トークンによって参照されるメソッドと、指定した EventProp トークンによって参照されるペアのプロパティおよびイベントの間のリレーションシップを示すフラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `mb`  
 からセマンティックロール情報を取得するメソッドを表す MethodDef トークン。  
  
 `tkEventProp`  
 からメソッドのロールを取得するための、ペアのプロパティとイベントを表すトークン。  
  
 `pdwSemanticsFlags`  
 入出力関連付けられているセマンティクスフラグへのポインター。 この値は、 [CorMethodSemanticsAttr](cormethodsemanticsattr-enumeration.md) 列挙体のビットマスクです。  
  
## <a name="remarks"></a>注釈  

 [IMetaDataEmit::D efineProperty](imetadataemit-defineproperty-method.md)メソッドは、メソッドのセマンティクスフラグを設定します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
