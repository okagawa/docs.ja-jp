---
title: ICLRStrongName::StrongNameCompareAssemblies メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
ms.openlocfilehash: ddcbe84053aa7f4cafd81e905f8aef988f92875e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685702"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a>ICLRStrongName::StrongNameCompareAssemblies メソッド

厳密な名前の署名に基づいて 2 つのアセンブリが異なるかどうかが判定されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `wszAssembly1`  
 から最初のアセンブリへのパス。  
  
 `wszAssembly2`  
 から2番目のアセンブリへのパス。  
  
 `pdwResult`  
 入出力次のいずれかの値です。  
  
- `SN_CMP_DIFFERENT` (0)-アセンブリに異なるデータが含まれることを指定します。  
  
- `SN_CMP_IDENTICAL` (1)-署名やチェックサムなど、アセンブリがまったく同じであることを指定します。  
  
- `SN_CMP_SIGONLY` (2)-アセンブリが署名とチェックサムのみで異なることを指定します。  
  
## <a name="return-value"></a>戻り値  

 `S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="remarks"></a>注釈  

 アセンブリの厳密な名前の署名は、アセンブリのテキスト名、バージョン、カルチャ、および公開キートークンで構成されます。  
  
## <a name="see-also"></a>関連項目

- [ICLRStrongName インターフェイス](iclrstrongname-interface.md)
