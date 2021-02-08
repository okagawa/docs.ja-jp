---
description: '詳細について: ICLRStrongName:: StrongNameHashSize メソッド'
title: ICLRStrongName::StrongNameHashSize メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameHashSize
helpviewer_keywords:
- ICLRStrongName::StrongNameHashSize method [.NET Framework hosting]
- StrongNameHashSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 4a05ee56-08e4-4f3a-86a9-9b52083d5c0f
topic_type:
- apiref
ms.openlocfilehash: 74781f0eaec720a84a242e6a9637036408652601
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799591"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a>ICLRStrongName::StrongNameHashSize メソッド

指定したハッシュ アルゴリズムを使用して、ハッシュに必須のバッファー サイズが取得されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ulHashAlg`  
 からバッファーサイズを計算するために使用されるハッシュアルゴリズム。  
  
 `pcbSize`  
 入出力返されたバッファーサイズ (バイト単位)。  
  
## <a name="return-value"></a>戻り値  

 `S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRStrongName インターフェイス](iclrstrongname-interface.md)
