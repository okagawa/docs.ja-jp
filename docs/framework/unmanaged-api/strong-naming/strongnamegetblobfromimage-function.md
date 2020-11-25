---
title: StrongNameGetBlobFromImage 関数
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
ms.openlocfilehash: 3a84221f94bad76d69f0dc67fe695ada3f3862f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732243"
---
# <a name="strongnamegetblobfromimage-function"></a>StrongNameGetBlobFromImage 関数

指定したメモリ アドレスにあるアセンブリ イメージのバイナリ表現が取得されます。  
  
 この関数は非推奨とされます。 代わりに [ICLRStrongName:: StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pbBase`  
 からマップされたアセンブリマニフェストのメモリアドレス。  
  
 `dwLength`  
 からにあるイメージのサイズ (バイト単位) `pbBase` 。  
  
 `pbBlob`  
 からイメージのバイナリ表現を格納するバッファー。  
  
 `pcbBlob`  
 [入力、出力]要求された最大サイズ (バイト単位) `pbBlob` 。 戻り時に、の実際のサイズ (バイト単位) `pbBlob` 。  
  
## <a name="return-value"></a>戻り値  

 `true` 正常に完了した場合は。それ以外の場合は `false` 。  
  
## <a name="remarks"></a>注釈  

 関数が `StrongNameGetBlobFromImage` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameGetBlobFromImage メソッド](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [StrongNameGetBlob メソッド](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
