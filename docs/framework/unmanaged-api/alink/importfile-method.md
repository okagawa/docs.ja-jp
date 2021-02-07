---
description: 詳細については、「ImportFile メソッド」を参照してください。
title: ImportFile メソッド
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
ms.openlocfilehash: 82c9c7de7cd739ee205dc3695ea651643d01ea3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718162"
---
# <a name="importfile-method"></a>ImportFile メソッド

アセンブリとバインドされていないモジュールをインポートします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `pszFilename`  
 インポートするファイルの完全修飾名。  
  
 `pszTargetName`  
 アセンブリにリンクされているファイルの名前を変更するために使用できる省略可能な出力ファイル名です。  
  
 `fSmartImport`  
 TRUE の場合、ImportTypes が使用されます。それ以外の場合は、インポートを手動で実行する必要があります。  
  
 `pImportToken`  
 一意のファイル ID が格納されるトークンへのポインター。 ファイルには、アセンブリまたはファイルを指定できます。  
  
 `ppAssemblyScope`  
 [IMetaDataAssemblyImport インターフェイス](../metadata/imetadataassemblyimport-interface.md)へのポインターを受け取ります。 ファイルがアセンブリでない場合は NULL を指定できます。  
  
 `pdwCountOfScopes`  
 インポートされたファイルまたはスコープの数へのポインター。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK を返します。  
  
## <a name="requirements"></a>要件  

 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
