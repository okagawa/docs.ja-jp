---
title: IMetaDataImport2::GetVersionString メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
ms.openlocfilehash: 3e62b1177c0161883ad03086723cc43b71292df5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702564"
---
# <a name="imetadataimport2getversionstring-method"></a>IMetaDataImport2::GetVersionString メソッド

アセンブリのビルドに使用されたランタイムのバージョン番号を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pwzBuf`  
 入出力バージョンを指定する文字列を格納する配列。  
  
 `ccBufSize`  
 から配列のサイズ (ワイド文字単位) `pwzBuf` 。  
  
 `pccBufSize`  
 入出力配列内で返された、null 終端文字を含むワイド文字の数 `pwzBuf` 。  
  
## <a name="remarks"></a>注釈  

 メソッドは、 `GetVersionString` 現在のメタデータスコープの組み込みバージョンを取得します。 スコープが一度も保存されていない場合は、ビルドされたバージョンがないため、空の文字列が返されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
