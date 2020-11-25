---
title: StrongNameErrorInfo 関数
ms.date: 03/30/2017
api_name:
- StrongNameErrorInfo
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameErrorInfo
helpviewer_keywords:
- StrongNameErrorInfo function [.NET Framework strong naming]
ms.assetid: e91bf8c3-7c26-4732-938e-2e5b04abfc99
topic_type:
- apiref
ms.openlocfilehash: 90abfcd573795ae529714e21b13f90d6e15c7dad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732269"
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo 関数

厳密な名前の関数のいずれかに基づいて最後に発生したエラー コードが取得されます。  
  
 この関数は非推奨とされます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT StrongNameErrorInfo ();
```  
  
## <a name="return-value"></a>戻り値  

 厳密な名前関数のいずれかによって設定された最後の COM エラーコード。  
  
## <a name="remarks"></a>注釈  

 厳密な名前のメソッドのほとんどは、 `true` 正常に完了したかどうかを示す単純な値を返し `false` ます。 関数を使用し `StrongNameErrorInfo` て、厳密な名前関数によって生成された最後のエラーを指定する HRESULT を取得します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
