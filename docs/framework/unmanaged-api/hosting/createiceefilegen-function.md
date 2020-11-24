---
title: CreateICeeFileGen 関数
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
ms.openlocfilehash: 454cfa2dd1b676f32649050625b1074fbd776d54
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673333"
---
# <a name="createiceefilegen-function"></a>CreateICeeFileGen 関数

[ICeeFileGen](iceefilegen-class.md)オブジェクトを作成します。  
  
 この関数は .NET Framework 4 で非推奨とされました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ceeFileGen`  
 入出力新しいオブジェクトのアドレスへのポインター `ICeeFileGen` 。  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、標準の COM エラーコードを返します。  
  
## <a name="remarks"></a>注釈  

 `ICeeFileGen`オブジェクトは、共通言語ランタイム (CLR) の移植可能な実行可能 (PE) ファイルを作成するために使用されます。  
  
 完了したら、 [DestroyICeeFileGen](destroyiceefilegen-function.md) 関数を呼び出してオブジェクトを破棄し `ICeeFileGen` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** ICeeFileGen  
  
 **ライブラリ:** MSCorPE.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](deprecated-clr-hosting-functions.md)
