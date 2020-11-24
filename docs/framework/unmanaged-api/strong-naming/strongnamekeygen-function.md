---
title: StrongNameKeyGen 関数
ms.date: 03/30/2017
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
ms.openlocfilehash: 4844701784a3e6a1008a5deb2bdff3b3ba47aa7e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691410"
---
# <a name="strongnamekeygen-function"></a>StrongNameKeyGen 関数

厳密な名前を使用するために新しい公開/秘密キーの組が作成されます。  
  
 この関数は非推奨とされます。 代わりに [ICLRStrongName:: StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `wszKeyContainer`  
 から要求されたキーコンテナー名。 `wszKeyContainer` は空でない文字列である必要があります。または、一時名を生成する場合は null にする必要があります。  
  
 `dwFlags`  
 からキーを登録したままにするかどうかを指定します。 サポートされている値を次に示します。  
  
- 0x00000000- `wszKeyContainer` が null の場合に、一時キーコンテナー名を生成するために使用されます。  
  
- 0x00000001 ( `SN_LEAVE_KEY` )-キーを登録したままにすることを指定します。  
  
 `ppbKeyBlob`  
 入出力返された公開/秘密キーのペア。  
  
 `pcbKeyBlob`  
 入出力のサイズ (バイト単位) `ppbKeyBlob` 。  
  
## <a name="return-value"></a>戻り値  

 `true` 正常に完了した場合は。それ以外の場合は `false` 。  
  
## <a name="remarks"></a>注釈  

 関数は、 `StrongNameKeyGen` 1024 ビットのキーを作成します。 キーが取得されたら、 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 関数を呼び出して、割り当てられたメモリを解放する必要があります。  
  
 関数が `StrongNameKeyGen` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameKeyGen メソッド](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [StrongNameKeyGenEx メソッド](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
