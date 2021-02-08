---
description: '詳細について: IMetaDataImport:: GetMethodSemantics メソッド'
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
ms.openlocfilehash: 2b17e2ffaeef3a451850ce2cc9c4861d68df3a81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783860"
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
  
## <a name="remarks"></a>解説  

 [IMetaDataEmit::D efineProperty](imetadataemit-defineproperty-method.md)メソッドは、メソッドのセマンティクスフラグを設定します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
