---
description: '詳細情報: 動機チェーン:: GetReason メソッド'
title: ICorDebugChain::GetReason メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- GetReason
helpviewer_keywords:
- GetReason method [.NET Framework debugging]
- ICorDebugChain::GetReason method [.NET Framework debugging]
ms.assetid: 9f9f62b9-113a-4a98-8f9b-b593cef27b03
topic_type:
- apiref
ms.openlocfilehash: 0952d09db6d43f7970ba9e8c46c409fb2cd4b131
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694970"
---
# <a name="icordebugchaingetreason-method"></a>ICorDebugChain::GetReason メソッド

この呼び出しチェーンの genesis の理由を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pReason`  
 入出力この呼び出しチェーンの genesis の理由を示す、CorDebugChainReason 列挙体の値 (ビットごとの組み合わせ) へのポインター。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
