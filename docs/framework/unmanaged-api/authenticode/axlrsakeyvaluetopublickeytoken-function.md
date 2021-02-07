---
description: '詳細情報: _AxlRSAKeyValueToPublicKeyToken 関数'
title: _AxlRSAKeyValueToPublicKeyToken 関数
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
topic_type:
- apiref
ms.openlocfilehash: 01fc4cdc1d9985375748307ca2d7fff97191c908
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747271"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a>\_AxlRSAKeyValueToPublicKeyToken 関数

Modulus および Exponent を、厳密な名前の公開キー トークンに変換します。

## <a name="syntax"></a>構文

```cpp
HRESULT _AxlRSAKeyValueToPublicKeyToken (
    [in]  PCRYPT_DATA_BLOB pModulusBlob,
    [in]  PCRYPT_DATA_BLOB pExponentBlob,
    [out] LPWSTR           *ppwszPublicKeyToken
);
```

## <a name="parameters"></a>パラメーター

 `pModulusBlob`\
 からBase64 でエンコードされた剰余 blob ( \<Modulus> 要素から)。  [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob)構造を参照してください。

 `pExponentBlob`\
 からBase64 でエンコードされた指数 (要素からの \<Exponent> ) blob。 [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob)構造を参照してください。

 `ppwszPublicKeyToken`\
 [out] 16 進エンコードされた公開キー トークンを受け取るための WCHAR * へのポインター。

## <a name="return-value"></a>戻り値

 関数が成功した場合は `S_OK`。 それ以外の場合はエラー コードを返します。

## <a name="requirements"></a>要件

**アセンブリ**: clr.dll

## <a name="see-also"></a>関連項目

- [Authenticode](index.md)
