---
description: '詳細情報: テキストフレーム:: GetCaller メソッド'
title: ICorDebugFrame::GetCaller メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
ms.openlocfilehash: a042341f6edfa0e8f6ca00f758107852f9e381cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693045"
---
# <a name="icordebugframegetcaller-method"></a>ICorDebugFrame::GetCaller メソッド

このフレームを呼び出した現在のチェーン内のテキストボックスオブジェクトへのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppFrame`  
 入出力呼び出し元のフレームを表すオブジェクトのアドレスへのポインター `ICorDebugFrame` 。 呼び出されたフレームが現在のチェーンの最も外側のフレームである場合、この値は null になります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
