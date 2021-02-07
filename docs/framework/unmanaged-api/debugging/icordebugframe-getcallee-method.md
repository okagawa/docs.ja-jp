---
description: '詳細情報: テキストフレーム:: GetCallee 先メソッド'
title: ICorDebugFrame::GetCallee メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
ms.openlocfilehash: 85b64933cb2f180445b88f7b19f8b78f1788252e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693071"
---
# <a name="icordebugframegetcallee-method"></a>ICorDebugFrame::GetCallee メソッド

このフレームが呼び出された現在のチェーン内のテキストボックスオブジェクトへのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppFrame`  
 入出力呼び出されたフレームを表すオブジェクトのアドレスへのポインター `ICorDebugFrame` 。 呼び出し元のフレームが現在のチェーンの最も内側のフレームである場合、この値は null になります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
