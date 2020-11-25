---
title: GetPublicKeyToken メソッド
ms.date: 03/30/2017
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
ms.openlocfilehash: e41be6407076a2609a83a5be3b0c42d28914ec38
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720343"
---
# <a name="getpublickeytoken-method"></a>GetPublicKeyToken メソッド

指定されたキーキーまたはキーコンテナーの公開キートークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `pszKeyFile`  
 キーのファイル名。  
  
 `pszKeyContainer`  
 キーコンテナーの名前。  
  
 `pvPublicKeyToken`  
 キートークンを格納するアドレス。  
  
 `pcbPublicKeyToken`  
 によって示されるバッファーのサイズ (バイト単位) を指定し `pvPublicKeyToken` ます。 戻り時には、実際に使用されたバイト数が含まれます。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK を返します。  
  
## <a name="requirements"></a>要件  

 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink2 インターフェイス](ialink2-interface.md)
- [IALink インターフェイス](ialink-interface.md)
- [ALink API](index.md)
