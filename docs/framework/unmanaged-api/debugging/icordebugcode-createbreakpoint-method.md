---
description: '詳細情報: Okcode:: CreateBreakpoint ポイントメソッド'
title: ICorDebugCode::CreateBreakpoint メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
ms.openlocfilehash: a9285d59da3e3f34ea303413fca67bc39aff9e32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711376"
---
# <a name="icordebugcodecreatebreakpoint-method"></a>ICorDebugCode::CreateBreakpoint メソッド

このコードセグメントの指定したオフセット位置にブレークポイントを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `offset`  
 からブレークポイントを作成する位置のオフセット。  
  
 `ppBreakpoint`  
 入出力ブレークポイントを表す "いいね! ブレークポイント" オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 ブレークポイントがアクティブになる前に、そのブレークポイントをプロセスオブジェクトに追加する必要があります。  
  
 このコードが Microsoft 中間言語 (MSIL) コードで、just-in-time (JIT) でコンパイルされたネイティブバージョンのコードがある場合、ブレークポイントは JIT コンパイルコードにも適用されます。 (コードが後で JIT コンパイルされる場合も同様です)。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
