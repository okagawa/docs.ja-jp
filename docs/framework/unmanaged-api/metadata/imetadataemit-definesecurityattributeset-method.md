---
description: '詳細について: IMetaDataEmit::D efineSecurityAttributeSet メソッド'
title: IMetaDataEmit::DefineSecurityAttributeSet メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineSecurityAttributeSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet
helpviewer_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet method [.NET Framework metadata]
- DefineSecurityAttributeSet method [.NET Framework metadata]
ms.assetid: 27064ca2-4186-4433-90a7-3b297785e891
topic_type:
- apiref
ms.openlocfilehash: 3512857ca23d65389b0e150bd24234d272ddd9b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784055"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a>IMetaDataEmit::DefineSecurityAttributeSet メソッド

指定したトークンによって参照されるオブジェクトにアタッチするセキュリティアクセス許可のセットを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineSecurityAttributeSet (
    [in]  mdToken       tkObj,
    [in]  COR_SECATTR   rSecAttrs[],
    [in]  ULONG         cSecAttrs,
    [out] ULONG         *pulErrorAttr
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `tkObj`  
 からセキュリティ情報がアタッチされるトークン。  
  
 `rSecAttrs`  
 から `COR_SECATTR` 構造体の配列。  
  
 `cSecAttrs`  
 から内の要素の数 `rSecAttrs` 。  
  
 `pulErrorAttr`  
 入出力メソッドが失敗した場合、は、 `rSecAttrs` 問題の原因となった要素ののインデックスを指定します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](imetadataemit2-interface.md)
