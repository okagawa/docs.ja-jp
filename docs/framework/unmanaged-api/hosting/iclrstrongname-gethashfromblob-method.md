---
description: '詳細について: ICLRStrongName:: GetHashFromBlob メソッド'
title: ICLRStrongName::GetHashFromBlob メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromBlob
helpviewer_keywords:
- ICLRStrongName::GetHashFromBlob method [.NET Framework hosting]
- GetHashFromBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: f91d0f89-f356-49ac-aafb-50fad963c13d
topic_type:
- apiref
ms.openlocfilehash: 20d03184f57e77741e656575038e426ee37968f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637067"
---
# <a name="iclrstrongnamegethashfromblob-method"></a>ICLRStrongName::GetHashFromBlob メソッド

指定したハッシュ アルゴリズムを使用して、指定したメモリ アドレスにあるアセンブリのハッシュが取得されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pbBlob`  
 からハッシュされるメモリブロックのアドレスへのポインター。  
  
 `cchBlob`  
 からメモリブロックの長さ (バイト単位)。  
  
 `piHashAlg`  
 [入力、出力]ハッシュアルゴリズムを指定する定数。 既定のアルゴリズムには0を使用します。  
  
 `pbHash`  
 入出力返されたハッシュバッファー。  
  
 `cchHash`  
 から要求された最大サイズ `pbHash` 。  
  
 `pchHash`  
 入出力返されたのサイズ (バイト単位) `pbHash` 。  
  
## <a name="return-value"></a>戻り値  

 `S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRStrongName インターフェイス](iclrstrongname-interface.md)
