---
description: '詳細については、次を参照してください: いいね Value インターフェイス'
title: ICorDebugHandleValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
ms.openlocfilehash: 3bdb1f5668be283d8722c15f4779adfe4d7b3a2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692044"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue インターフェイス

デバッガーがガベージコレクションのハンドルを作成した参照値を表す、値のサブクラス。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Dispose メソッド](icordebughandlevalue-dispose-method.md)|`ICorDebugHandleValue`インターフェイスポインターを明示的に解放せずに、このオブジェクトによって参照されるハンドルを解放します。|  
|[GetHandleType メソッド](icordebughandlevalue-gethandletype-method.md)|このによって参照されるハンドルの種類を記述する CorDebugHandleType 値を取得し `ICorDebugHandleValue` ます。|  
  
## <a name="remarks"></a>解説  

 `ICorDebugReferenceValue`デバッグ対象のコードの実行が中断された場合、オブジェクトは無効になります。 は、 `ICorDebugHandleValue` 明示的に解放されるまで、中断および継続による参照を保持します。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
