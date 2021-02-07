---
description: '詳細については、次を参照してください: IAssemblyCacheItem:: CreateStream メソッド'
title: IAssemblyCacheItem::CreateStream メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
ms.openlocfilehash: 89592d8fe1a7f43a7da20dd10883881c3339f088
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760873"
---
# <a name="iassemblycacheitemcreatestream-method"></a>IAssemblyCacheItem::CreateStream メソッド

指定された名前と形式を使用してストリームを作成します。

## <a name="syntax"></a>構文

```cpp
HRESULT CreateStream (
    [in]  DWORD dwFlags,
    [in]  LPCWSTR pszStreamName,
    [in]  DWORD dwFormat,
    [in]  DWORD dwFormatFlags,
    [out] IStream **ppIStream,
    [in, optional] ULARGE_INTEGER *puliMaxSize
);
```

## <a name="parameters"></a>パラメーター

`dwFlags`\
からFusion に定義されているフラグ。

`pszStreamName`\
から作成されるストリームの名前。

`dwFormat`\
からストリーム配信されるファイルの形式。

`dwFormatFlags`\
からFusion に定義されている形式固有のフラグ。

`ppIStream`\
入出力返された [IStream](/windows/desktop/api/objidl/nn-objidl-istream) インスタンスのアドレスへのポインター。

`puliMaxSize`\
[in、optional]によって参照されるストリームの最大サイズ `ppIStream` 。

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

**ヘッダー:** Fusion. h

**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>関連項目

- [IAssemblyCacheItem インターフェイス](iassemblycacheitem-interface.md)
