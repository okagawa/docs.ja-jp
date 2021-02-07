---
description: '詳細については、次を参照してください: いいね:: GetStackRange メソッド'
title: ICorDebugChain::GetStackRange メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
ms.openlocfilehash: 066dda06564655350d799dabb54acd622b828172
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694931"
---
# <a name="icordebugchaingetstackrange-method"></a>ICorDebugChain::GetStackRange メソッド

このチェーンのスタックセグメントのアドレス範囲を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pStart`  
 入出力 `CORDB_ADDRESS` スタックセグメントの開始アドレスを示す値へのポインター。  
  
 `pEnd`  
 入出力 `CORDB_ADDRESS` スタックセグメントの終了アドレスを示す値へのポインター。  
  
## <a name="remarks"></a>解説  

 数値の範囲は、スタックフレームの位置を比較する場合にのみ意味があります。 実際にスタックに格納されている内容について、想定を行うことはできません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
