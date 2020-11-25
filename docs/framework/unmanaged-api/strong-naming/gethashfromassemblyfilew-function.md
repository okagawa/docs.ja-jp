---
title: GetHashFromAssemblyFileW 関数
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
ms.openlocfilehash: b895c77850c0457fd2a152c1128c016093599f76
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730982"
---
# <a name="gethashfromassemblyfilew-function"></a>GetHashFromAssemblyFileW 関数

指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュ値が取得されます。 アセンブリファイルへのパスは、Unicode 文字列として指定する必要があります。  
  
 この関数は非推奨とされます。 代わりに [ICLRStrongName:: GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `wszFilePath`  
 からハッシュされるファイルへのパス。 このパラメーターは Unicode 文字列である必要があります。  
  
 `piHashAlg`  
 [入力、出力]ハッシュアルゴリズムを指定する定数。 既定のハッシュアルゴリズムには0を使用します。  
  
 `pbHash`  
 入出力返されたハッシュバッファー。  
  
 `cchHash`  
 から要求された最大サイズ `pbHash` 。  
  
 `pchHash`  
 入出力の返されたサイズ (バイト単位) `pbHash` 。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetHashFromAssemblyFileW メソッド](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [GetHashFromAssemblyFile メソッド](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
