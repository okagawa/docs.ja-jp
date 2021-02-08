---
description: '詳細については、次を参照してください: いいね。'
title: ICorDebugVariableHomeEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
ms.openlocfilehash: c56c68a6b5f9d329fe8af23f47b40fa629bfe3ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790621"
---
# <a name="icordebugvariablehomeenum-interface"></a>ICorDebugVariableHomeEnum インターフェイス

関数のローカル変数および引数に列挙子を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[次のメソッド](icordebugvariablehomeenum-next-method.md)|関数内のローカル変数および引数に関する情報を格納している指定された数の表示変数 [home](icordebugvariablehome-interface.md) インスタンスを取得します。|  
  
## <a name="remarks"></a>解説  

 `ICorDebugVariableHomeEnum`インターフェイスは、ICorDebugEnum インターフェイスを実装します。  
  
 `ICorDebugVariableHomeEnum`インスタンスには、 [ICorDebugCode4:: EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md)メソッドを呼び出すことによって、表示[変数 home](icordebugvariablehome-interface.md)インスタンスが設定されます。 コレクション内 [の各は](icordebugvariablehome-interface.md) 、関数のローカル変数または引数を表します。 コレクション内  [のオブジェクトを](icordebugvariablehome-interface.md) 列挙するには、 [次](icordebugvariablehomeenum-next-method.md) のように指定します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugVariableHome インターフェイス](icordebugvariablehome-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
