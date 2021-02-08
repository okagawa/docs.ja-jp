---
description: '詳細について: IMetaDataImport:: GetRVA メソッド'
title: IMetaDataImport::GetRVA メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: 8d6439bcad50a6311e7bb1408f4c86144a5026ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789165"
---
# <a name="imetadataimportgetrva-method"></a>IMetaDataImport::GetRVA メソッド

指定したトークンによって表されるメソッドまたはフィールドの相対仮想アドレス (RVA) および実装フラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `tk`  
 からRVA を返すコードオブジェクトを表す MethodDef または FieldDef のメタデータトークン。 トークンが FieldDef の場合、フィールドはグローバル変数である必要があります。  
  
 `pulCodeRVA`  
 入出力トークンによって表されるコードオブジェクトの相対仮想アドレスへのポインター。  
  
 `pdwImplFlags`  
 入出力メソッドの実装フラグへのポインター。 この値は [Cormethodimpl](cormethodimpl-enumeration.md) 列挙子のビットマスクです。 の値は、 `pdwImplFlags` `tk` が MethodDef トークンの場合にのみ有効です。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
