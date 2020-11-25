---
title: IMetaDataAssemblyImport::FindExportedTypeByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindExportedTypeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type:
- apiref
ms.openlocfilehash: b1672d98d76241e5af4b6b60a38785f1278e15a8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731593"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a>IMetaDataAssemblyImport::FindExportedTypeByName メソッド

名前と外側の型を指定して、エクスポートされた型へのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `szName`  
 からエクスポートされた型の名前。  
  
 `mdtExportedType`  
 からエクスポートする型の外側のクラスのメタデータトークン。 要求されたエクスポート型が入れ子にされた型では `mdExportedTypeNil` ない場合、この値はです。  
  
 `ptkExportedType`  
 入出力エクスポートされた `mdExportedType` 型を表すトークンへのポインター。  
  
## <a name="remarks"></a>注釈  

 メソッドは、 `FindExportedTypeByName` 参照を解決するために共通言語ランタイムによって採用されている標準の規則を使用します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyImport インターフェイス](imetadataassemblyimport-interface.md)
- [ランタイムがアセンブリを検索する方法](../../deployment/how-the-runtime-locates-assemblies.md)
