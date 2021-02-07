---
description: '詳細情報: ImportFileEx2 メソッド'
title: ImportFileEx2 メソッド
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx2
helpviewer_keywords:
- ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type:
- apiref
ms.openlocfilehash: 0968318ab7e416e56b71f2f30f2745d538d0ff8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718006"
---
# <a name="importfileex2-method"></a>ImportFileEx2 メソッド

アセンブリとバインドされていないモジュールをインポートします。 このメソッドは [Importfile メソッド](importfile-method.md)に似ていますが、インポートされるファイルがディスク上に存在しない場合でも機能します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `pszFilename`  
 インポートするファイルの名前。  
  
 `pszTargetName`  
 ターゲットファイルの名前 (省略可能)。  
  
 `pAssemblyScopeIn`  
 省略可能なインポートスコープ [IMetaDataAssemblyImport インターフェイス](../metadata/imetadataassemblyimport-interface.md) インターフェイス。  
  
 `fSmartImport`  
 TRUE の場合、ImportTypes が使用されます。それ以外の場合は、インポートを手動で実行する必要があります。  
  
 `dwOpenFlags`  
 [Openscope メソッド](../metadata/imetadatadispenser-openscope-method.md)に渡されるフラグ。  
  
 `pImportToken`  
 アセンブリまたはファイルの一意の ID を受け取ります。  
  
 `ppAssemblyScope`  
 アセンブリインポートスコープ [IMetaDataAssemblyImport インターフェイス](../metadata/imetadataassemblyimport-interface.md) インターフェイスを受け取ります。 ファイルがアセンブリでない場合は NULL を指定できます。  
  
 `pdwCountOfScopes`  
 インポートされたファイルまたはスコープの数を受け取ります。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK を返します。  
  
## <a name="requirements"></a>要件  

 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink2 インターフェイス](ialink2-interface.md)
- [IALink インターフェイス](ialink-interface.md)
- [ALink API](index.md)
