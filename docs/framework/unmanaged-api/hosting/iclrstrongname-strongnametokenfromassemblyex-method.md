---
title: ICLRStrongName::StrongNameTokenFromAssemblyEx メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type:
- apiref
ms.openlocfilehash: e504aa067d51ec62d42f019c3a9e40538e374ea1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762618"
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a>ICLRStrongName::StrongNameTokenFromAssemblyEx メソッド
指定したアセンブリファイルから厳密な名前トークンを作成し、トークンが表す公開キーを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 からアセンブリのポータブル実行可能 (PE) ファイルへのパス。  
  
 `ppbStrongNameToken`  
 入出力返された厳密な名前トークン。  
  
 `pcbStrongNameToken`  
 入出力厳密な名前トークンのサイズ (バイト単位)。  
  
 `ppbPublicKeyBlob`  
 入出力返された公開キー。  
  
 `pcbPublicKeyBlob`  
 入出力公開キーのサイズ (バイト単位)。  
  
## <a name="return-value"></a>戻り値  
 `S_OK`メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの[一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values)」を参照してください)。  
  
## <a name="remarks"></a>解説  
 厳密な名前トークンは、公開キーの短縮形です。 トークンは、アセンブリの署名に使用される公開キーから作成された64ビットのハッシュです。 トークンはアセンブリの厳密な名前の一部であり、アセンブリメタデータから読み取ることができます。  
  
 キーを取得してトークンを作成したら、 [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md)メソッドを呼び出して、割り当てられたメモリを解放する必要があります。  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameTokenFromAssembly メソッド](iclrstrongname-strongnametokenfromassembly-method.md)
- [ICLRStrongName インターフェイス](iclrstrongname-interface.md)
