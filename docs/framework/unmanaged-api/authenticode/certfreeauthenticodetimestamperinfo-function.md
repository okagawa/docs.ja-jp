---
description: '詳細情報: CertFreeAuthenticodeTimestamperInfo 関数'
title: CertFreeAuthenticodeTimestamperInfo 関数
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeTimestamperInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
topic_type:
- apiref
ms.openlocfilehash: 5234a90ea1d0272a7409b1b0b4def2160b77a513
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772940"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a>CertFreeAuthenticodeTimestamperInfo 関数

[AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md)構造に割り当てられたリソースを解放します。

## <a name="syntax"></a>構文

```cpp
HRESULT CertFreeAuthenticodeTimestamperInfo (
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo
);
```

## <a name="parameters"></a>パラメーター

 `pTimestamperInfo`\
 [入力、出力] 解放されるタイム スタンパー情報。 [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md)構造を参照してください。

## <a name="return-value"></a>戻り値

 関数が成功した場合は `S_OK`。 それ以外の場合はエラー コードを返します。

## <a name="requirements"></a>要件

**アセンブリ**: clr.dll

## <a name="see-also"></a>関連項目

- [Authenticode](index.md)
