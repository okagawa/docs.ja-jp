---
description: '詳細情報: StrongNameSignatureVerificationEx 関数'
title: StrongNameSignatureVerificationEx 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
ms.openlocfilehash: 9e20044e9c3caef8c2276ac5f390269ee978d55b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794534"
---
# <a name="strongnamesignatureverificationex-function"></a>StrongNameSignatureVerificationEx 関数

指定したパスにあるアセンブリ マニフェストに厳密な名前の署名が含まれるかどうかを示す値が取得されます。  
  
 この関数は非推奨とされます。 代わりに [ICLRStrongName:: StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `wszFilePath`  
 から検証するアセンブリの移植可能な実行可能ファイル (.exe または .dll) のパス。  
  
 `fForceVerification`  
 [入力] `true` レジストリ設定を上書きする必要がある場合でも、検証を実行するにはそれ以外の場合は `false` 。  
  
 `pfWasVerified`  
 [出力] `true` 厳密な名前の署名が検証された場合は。それ以外の場合は `false` 。 `pfWasVerified``false`レジストリ設定によって検証が成功した場合は、もに設定されます。  
  
## <a name="return-value"></a>戻り値  

 `true` 検証が成功した場合は、それ以外の場合は `false` 。  
  
## <a name="remarks"></a>解説  

 `StrongNameSignatureVerificationEx`[StrongNameSignatureVerification](strongnamesignatureverification-function.md)関数と同様の機能を提供します。 ただし、2番目の入力パラメーターとの出力パラメーター `StrongNameSignatureVerificationEx` は、 `BOOLEAN` の代わりに型に `DWORD` なります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ:** mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureVerificationEx メソッド](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [StrongNameSignatureVerification メソッド](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
