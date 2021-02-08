---
description: 詳細については、「ICorDebugILFrame3 インターフェイス」を参照してください。
title: ICorDebugILFrame3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type:
- apiref
ms.openlocfilehash: a34a3f0941871a2d0a63fb2d9f78ccb7ff455866
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791258"
---
# <a name="icordebugilframe3-interface"></a>ICorDebugILFrame3 インターフェイス

関数の戻り値をカプセル化するメソッドを提供します。 `ICorDebugILFrame3` は、ICorDebugILFrame2 インターフェイスとインターフェイスを論理的に拡張したものです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetReturnValueForILOffset メソッド](icordebugilframe3-getreturnvalueforiloffset-method.md)|関数の戻り値をカプセル化する ICorDebugValue オブジェクトを取得します。|  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugCode3 インターフェイス](icordebugcode3-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
