---
description: '詳細情報: SetAssemblyFile メソッド'
title: SetAssemblyFile メソッド
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
ms.openlocfilehash: 943e0600b9781aeaf45cc26e39bd8a8b33a783c2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662495"
---
# <a name="setassemblyfile-method"></a>SetAssemblyFile メソッド

ビルドされるアセンブリの名前を割り当てます。 非バインドモジュールの生成時には使用しません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `pszFilename`  
 マニフェストファイルの完全修飾名。  
  
 `pEmitter`  
 [IMetaDataEmit インターフェイス](../metadata/imetadataemit-interface.md)インターフェイスへのポインター。  
  
 `afFlags`  
 [Assemblyflags 列挙型](../metadata/assemblyflags-enumeration.md)で定義されているフラグ。  
  
 `pAssemblyID`  
 結果として得られるアセンブリの ID へのポインター。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK を返します。  
  
## <a name="requirements"></a>要件  

 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
