---
title: StrongNameGetBlob 関数
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
ms.openlocfilehash: 8f5cb89294004dfb1f020627ceb1edb58735f72c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732282"
---
# <a name="strongnamegetblob-function"></a>StrongNameGetBlob 関数

指定したアドレスにある実行可能ファイルのバイナリ表現が、指定したバッファーに入れられます。  
  
 この関数は非推奨とされます。 代わりに [ICLRStrongName:: StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `wszFilePath`  
 から読み込む実行可能ファイルへの有効なパス。  
  
 `pbBlob`  
 から実行可能ファイルの読み込み先のバッファー。  
  
 `pcbBlob`  
 [入力、出力]要求された最大サイズ (バイト単位) `pbBlob` 。 戻り時に、の実際のサイズ (バイト単位) `pbBlob` 。  
  
## <a name="return-value"></a>戻り値  

 `true` 正常に完了した場合は。それ以外の場合は `false` 。  
  
## <a name="remarks"></a>注釈  

 関数が `StrongNameGetBlob` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameGetBlob メソッド](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [StrongNameGetBlobFromImage メソッド](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
