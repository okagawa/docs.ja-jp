---
description: '詳細情報: AddImport メソッド'
title: AddImport メソッド
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
ms.openlocfilehash: 9dca26501e66313b0932caf1288db7c909154e1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638601"
---
# <a name="addimport-method"></a>AddImport メソッド

アセンブリにインポートを追加します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `AssemblyID`  
 補強するアセンブリの一意の ID。  
  
 `ImportToken`  
 インポートするファイルの [Importfile メソッド](importfile-method.md)から取得された一意の ID。  
  
 `dwFlags`  
 やなどの COM + FileDef フラグ `ffContainsNoMetaData` `ffWriteable` 。 `dwFlags` は、 [メソッド](../metadata/imetadataassemblyemit-definefile-method.md)に渡されます。  
  
 `pFileToken`  
 結果ファイルの ID を受け取るトークンへのポインター。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK を返します。  
  
## <a name="requirements"></a>要件  

 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
