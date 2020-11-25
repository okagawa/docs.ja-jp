---
title: StrongNameSignatureSize 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
ms.openlocfilehash: 6a2b3afe66f1eaa358c5f80de50f14ceb730048b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708479"
---
# <a name="strongnamesignaturesize-function"></a>StrongNameSignatureSize 関数

厳密な名前の署名のサイズが返されます。 `StrongNameSignatureSize` は、通常、コンパイラによって使用され、遅延署名されたアセンブリを作成するときにファイルで予約する領域の量を決定します。  
  
 この関数は非推奨とされます。 代わりに [ICLRStrongName:: StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a>パラメーター  

 `pbPublicKeyBlob`  
 から厳密な名前の署名を生成するために使用されるキーペアの公開部分を格納する [Publickeyblob](publickeyblob-structure.md) 型の構造体。  
  
 `cbPublicKeyBlob`  
 からのサイズ (バイト単位) `pbPublicKeyBlob` 。  
  
 `pcbSize`  
 から厳密な名前の署名を格納するために必要なバイト数。  
  
## <a name="return-value"></a>戻り値  

 `true` 正常に完了した場合は。それ以外の場合は `false` 。  
  
## <a name="remarks"></a>注釈  

 関数が `StrongNameSignatureSize` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureSize メソッド](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
