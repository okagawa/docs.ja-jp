---
description: '詳細については、次のページを参照してください: いい評価:: NewString メソッド'
title: ICorDebugEval::NewString メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
ms.openlocfilehash: 21eb49900d84cb1ad1f68a701998a4a778c3ef17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693838"
---
# <a name="icordebugevalnewstring-method"></a>ICorDebugEval::NewString メソッド

指定された内容を持つ新しい文字列インスタンスを割り当てます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `string`  
 から文字列のコンテンツへのポインター。  
  
## <a name="remarks"></a>解説  

 文字列は常に、スレッドが現在実行されているアプリケーションドメインで作成されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
