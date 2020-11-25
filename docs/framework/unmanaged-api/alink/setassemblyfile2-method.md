---
title: SetAssemblyFile2 メソッド
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
ms.openlocfilehash: 131f5d951e524ef48f2cfe1e3e88ef80ac21c452
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703682"
---
# <a name="setassemblyfile2-method"></a>SetAssemblyFile2 メソッド

新しいアセンブリのオプションとオプションの名前を設定します。 バインドされていないモジュールを生成する場合は、このメソッドを呼び出さないでください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `pszFilename`  
 マニフェストファイルの名前。  
  
 `pEmitter`  
 このファイルの[IMetaDataEmit2 インターフェイス](../metadata/imetadataemit2-interface.md)インターフェイス。  
  
 `afFlags`  
 [Assemblyflags 列挙体](../metadata/assemblyflags-enumeration.md)によって表されるオプション。  
  
 `pAssemblyID`  
 構築されるアセンブリの一意の ID を受け取ります。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK を返します。  
  
## <a name="requirements"></a>要件  

 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink2 インターフェイス](ialink2-interface.md)
- [IALink インターフェイス](ialink-interface.md)
- [ALink API](index.md)
