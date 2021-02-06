---
description: '詳細情報: StrongNameErrorInfo 関数'
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
ms.openlocfilehash: a02e5f3d101a34c8ed13cb0f70fd2e95d945cb4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646401"
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
  
## <a name="remarks"></a>解説  

 厳密な名前のメソッドのほとんどは、 `true` 正常に完了したかどうかを示す単純な値を返し `false` ます。 関数を使用し `StrongNameErrorInfo` て、厳密な名前関数によって生成された最後のエラーを指定する HRESULT を取得します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
