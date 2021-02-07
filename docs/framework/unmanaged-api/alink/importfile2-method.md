---
description: '詳細情報: ImportFile2 メソッド'
title: ImportFile2 メソッド
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
ms.openlocfilehash: 98da8ecf4bfc19e52c5a92e6509f6af49afbdd5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718058"
---
# <a name="importfile2-method"></a>ImportFile2 メソッド

アセンブリとバインドされていないモジュールをインポートします。 このメソッドは [Importfile メソッド](importfile-method.md)に似ていますが、インポートされるファイルがディスク上に存在しない場合でも機能します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `pszFilename`  
 インポートするファイルの名前。  
  
 `pszTargetName`  
 アセンブリにリンクされているファイルの名前を変更するために使用できる省略可能な出力ファイル名です。  
  
 `pAssemblyScopeIn`  
 省略可能なスコープ [IMetaDataAssemblyImport インターフェイス](../metadata/imetadataassemblyimport-interface.md) インターフェイス。  
  
 `fSmartImport`  
 TRUE の場合、ImportTypes が使用されます。それ以外の場合は、インポートを手動で実行する必要があります。  
  
 `pImportToken`  
 ファイルまたはアセンブリの ID を受け取ります。  
  
 `ppAssemblyScope`  
 [IMetaDataAssemblyImport インターフェイス](../metadata/imetadataassemblyimport-interface.md)インターフェイスを受け取ります。 ファイルがアセンブリでない場合は NULL です。  
  
 `pdwCountOfScopes`  
 インポートされたファイルまたはスコープの検出されたを受信します。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK を返します。  
  
## <a name="requirements"></a>要件  

 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
