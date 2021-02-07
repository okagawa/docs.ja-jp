---
description: '詳細について: IMetaDataConverter:: GetMetaDataFromTypeInfo メソッド'
title: IMetaDataConverter::GetMetaDataFromTypeInfo メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeInfo
helpviewer_keywords:
- GetMetaDataFromTypeInfo method [.NET Framework metadata]
- IMetaDataConverter::GetMetaDataFromTypeInfo method [.NET Framework metadata]
ms.assetid: d44484bb-23a3-49c3-9e46-69d0d9ab4f0f
topic_type:
- apiref
ms.openlocfilehash: 224be07463b19ed9e22bef1a9d454d91a8086304
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753628"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a>IMetaDataConverter::GetMetaDataFromTypeInfo メソッド

指定したインスタンスによって参照されるタイプライブラリのメタデータシグネチャを表す [IMetaDataImport](imetadataimport-interface.md) インスタンスへのポインターを取得し `ITypeInfo` ます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pITI`  
 から `ITypeInfo` タイプライブラリを参照するオブジェクトへのポインター。  
  
 `ppMDI`  
 入出力メタデータシグネチャを表すインスタンスのアドレスを受け取る場所へのポインター `IMetaDataImport` 。  
  
## <a name="requirements"></a>要件  

 **プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](imetadataemit-interface.md)
- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
