---
title: GetWin32ResBlob メソッド
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
ms.openlocfilehash: 03f6c97b4a5bbbdc0aeaf7b3f07277e66d7d0e9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684513"
---
# <a name="getwin32resblob-method"></a>GetWin32ResBlob メソッド

Win32 リソース blob を取得します。 アセンブリオプションを設定した後に、このメソッドを呼び出します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `AssemblyID`  
 アセンブリの ID。  
  
 `FileToken`  
 Win32 バージョンリソースの構築時に使用されるファイル名を取得するために使用されるファイルトークン  
  
 `fDll`  
 ファイルが DLL の場合は TRUE、EXE の場合は false。  
  
 `pszIconFile`  
 リソース blob に挿入するオプションアイコン。  
  
 `ppResBlob`  
 リソース blob を受信します。  
  
 `pcbResBlob`  
 Blob のサイズを受け取ります。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK を返します。  
  
## <a name="requirements"></a>要件  

 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
