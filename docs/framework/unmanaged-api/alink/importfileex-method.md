---
description: '詳細情報: ImportFileEx メソッド'
title: ImportFileEx メソッド
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
ms.openlocfilehash: a8a7e5a142091bf7cc93f50a4ae20c59d800f3ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718019"
---
# <a name="importfileex-method"></a>ImportFileEx メソッド

指定したアセンブリまたはバインドされていないモジュールをインポートします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `pszFilename`  
 インポート元のファイルの完全修飾名。  
  
 `pszTargetName`  
 ターゲットファイルの名前 (省略可能)。  
  
 `fSmartImport`  
 TRUE の場合、ImportTypes が使用されます。それ以外の場合は、インポートを手動で実行する必要があります。  
  
 `dwOpenFlags`  
 [Openscope メソッド](../metadata/imetadatadispenser-openscope-method.md)に渡されるフラグ。  
  
 `pImportToken`  
 インポートされるファイルの ID を受け取ります。  
  
 `ppAssemblyScope`  
 アセンブリインポートスコープ [IMetaDataAssemblyImport インターフェイス](../metadata/imetadataassemblyimport-interface.md) インターフェイスを受け取ります。 ファイルがアセンブリでない場合、は NULL に設定されます。  
  
 `pdwCountOfScopes`  
 インポートされたファイルまたはスコープの数を受信します。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK を返します。  
  
## <a name="requirements"></a>要件  

 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink2 インターフェイス](ialink2-interface.md)
- [IALink インターフェイス](ialink-interface.md)
- [ALink API](index.md)
