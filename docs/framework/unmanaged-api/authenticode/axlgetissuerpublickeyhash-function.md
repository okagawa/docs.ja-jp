---
description: '詳細情報: _AxlGetIssuerPublicKeyHash 関数'
title: _AxlGetIssuerPublicKeyHash 関数
ms.date: 03/30/2017
api_name:
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
topic_type:
- apiref
ms.openlocfilehash: 586a072b33376a2fdade119fe3db0f48addfa3f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747362"
---
# <a name="_axlgetissuerpublickeyhash-function"></a>\_AxlGetIssuerPublicKeyHash 関数

指定された証明書の署名に使用する秘密キーに関連付けられている公開キーの SHA-1 ハッシュを取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT _AxlGetIssuerPublicKeyHash (
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,
    [out] LPWSTR                *ppwszPublicKeyHash
);
```

## <a name="parameters"></a>パラメーター

 `pChainContext`\
 [in] CSP 公開キー BLOB。 [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob)構造を参照してください。

 `ppwszPublicKeyHash`\
 [out] 16 進エンコードされた公開キー トークンを受け取るための WCHAR * へのポインター。

## <a name="return-value"></a>戻り値

 関数が成功した場合は `S_OK`、それ以外の場合は `S_FALSE`。

## <a name="requirements"></a>要件

**アセンブリ**: clr.dll

## <a name="see-also"></a>関連項目

- [Authenticode](index.md)
