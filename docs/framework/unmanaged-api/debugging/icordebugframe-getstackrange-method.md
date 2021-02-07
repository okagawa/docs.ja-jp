---
description: '詳細については、次を参照してください: テキスト枠:: GetStackRange メソッド'
title: ICorDebugFrame::GetStackRange メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
ms.openlocfilehash: 1f1278e0c00addc3c14f4e1c8d3ed5aad0381526
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692902"
---
# <a name="icordebugframegetstackrange-method"></a>ICorDebugFrame::GetStackRange メソッド

このスタックフレームの絶対アドレス範囲を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pStart`  
 入出力 `CORDB_ADDRESS` このオブジェクトによって表されるスタックフレームの開始アドレスを指定するへのポインター `ICorDebugFrame` 。  
  
 `pEnd`  
 入出力 `CORDB_ADDRESS` このオブジェクトによって表されるスタックフレームの終了アドレスを指定するへのポインター `ICorDebugFrame` 。  
  
## <a name="remarks"></a>解説  

 スタックのアドレス範囲は、複数のデバッグエンジンから収集されたインターリーブスタックトレースを piecing する場合に役立ちます。 数値の範囲は、スタックフレームの内容に関する情報を提供しません。 スタックフレームの位置を比較する場合にのみ意味があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
