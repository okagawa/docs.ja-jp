---
title: ICLRStrongName::GetHashFromAssemblyFile メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
ms.openlocfilehash: 0a15a4d237f63da54615ee1801e6cd39620e8274
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727862"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a>ICLRStrongName::GetHashFromAssemblyFile メソッド

指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュ値が取得されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `szFilePath`  
 からハッシュされるファイルへのパス。  
  
 `piHashAlg`  
 [入力、出力]ハッシュアルゴリズムを指定する定数。 既定のハッシュアルゴリズムには0を使用します。  
  
 `pbHash`  
 入出力返されたハッシュバッファー。  
  
 `cchHash`  
 から要求された最大サイズ `pbHash` 。  
  
 `pchHash`  
 入出力の返されたサイズ (バイト単位) `pbHash` 。  
  
## <a name="return-value"></a>戻り値  

 `S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetHashFromAssemblyFileW メソッド](iclrstrongname-gethashfromassemblyfilew-method.md)
- [ICLRStrongName インターフェイス](iclrstrongname-interface.md)
