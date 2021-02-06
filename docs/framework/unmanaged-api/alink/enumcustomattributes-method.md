---
description: '詳細情報: EnumCustomAttributes メソッド'
title: EnumCustomAttributes メソッド
ms.date: 03/30/2017
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type:
- apiref
ms.openlocfilehash: d5b537462745914903f0cdb1e9f4436f2c27a68d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638134"
---
# <a name="enumcustomattributes-method"></a>EnumCustomAttributes メソッド

アセンブリレベルのカスタム属性を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `hEnum`  
 列挙子のハンドル。  
  
 `tkType`  
 列挙する属性の型。 `mdTokenNill`すべての属性に使用します。  
  
 `rCustomValues`  
 カスタム属性トークンを受け取ります。  
  
 `cMax`  
 配列のサイズを指定し `rCustomValues` ます。  
  
 `pcCustomValues`  
 必要に応じて、トークンの値の数を受け取ります。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK を返します。  
  
## <a name="requirements"></a>要件  

 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
