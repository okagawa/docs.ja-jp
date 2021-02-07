---
description: '詳細については、次を参照してください: Okframe:: CreateStepper メソッド'
title: ICorDebugFrame::CreateStepper メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type:
- apiref
ms.openlocfilehash: 394418b89fd7a1c780a5bc33b97b8ef40bab8df2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693097"
---
# <a name="icordebugframecreatestepper-method"></a>ICorDebugFrame::CreateStepper メソッド

デバッガーがこのテキストフレームに対して相対的なステップ実行操作を実行できるようにするステッパを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppStepper`  
 入出力デバッガーが現在のフレームに対して相対的なステップ実行操作を実行できるようにする ICorDebugStepper オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 フレームがアクティブでない場合、通常、ステッパオブジェクトは、手順が完了する前にフレームに戻る必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
