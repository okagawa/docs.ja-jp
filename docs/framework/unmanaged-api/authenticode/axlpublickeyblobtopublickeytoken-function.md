---
description: '詳細情報: _AxlPublicKeyBlobToPublicKeyToken 関数'
title: _AxlPublicKeyBlobToPublicKeyToken 関数
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
topic_type:
- apiref
ms.openlocfilehash: df0b484bad64051eb892d4898a6c90777cc2d5cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781936"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a>\_AxlPublicKeyBlobToPublicKeyToken 関数

CSP PUBLICKEYBLOB 形式から厳密な名前の公開キー トークンを算出します。

## <a name="syntax"></a>構文

```cpp
HRESULT _AxlPublicKeyBlobToPublicKeyToken (
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,
    [out] LPWSTR                 *ppwszPublicKeyToken
);
```

## <a name="parameters"></a>パラメーター

 `pCspPublicKeyBlob`\
 [in] CSP 公開キー BLOB。

 `ppwszPublicKeyHash`\
 [out] 16 進エンコードされた公開キー ハッシュを受け取るための WCHAR * へのポインター。

## <a name="return-value"></a>戻り値

 関数が成功した場合は `S_OK`、それ以外の場合は `S_FALSE`。

## <a name="requirements"></a>要件

**アセンブリ**: clr.dll

## <a name="see-also"></a>関連項目

- [Authenticode](index.md)
