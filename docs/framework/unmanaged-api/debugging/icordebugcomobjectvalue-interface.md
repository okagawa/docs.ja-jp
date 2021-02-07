---
description: '詳細については、次を参照してください: いいね。'
title: ICorDebugComObjectValue のインターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
ms.openlocfilehash: 3c071c371ae6e330431630cfb1934b538d62efe6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710817"
---
# <a name="icordebugcomobjectvalue-interface"></a>ICorDebugComObjectValue のインターフェイス

ランタイム呼び出し可能ラッパー (RCW) に関連付けられている情報を取得するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetCachedInterfacePointers メソッド](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|現在の RCW でキャッシュされている生のインターフェイスポインターを取得します。|  
|[GetCachedInterfaceTypes メソッド](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|現在のオブジェクトで使用または使用されているインターフェイス型の列挙子を提供します。|  
  
## <a name="remarks"></a>解説  

 "ICorDebugValue" インターフェイスのインスタンスが RCW を表すかどうかを確認するために、デバッガーは `QueryInterface` を使用して "icordebugvalue" でを呼び出し `IID_ICorDebugComObjectValue` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
