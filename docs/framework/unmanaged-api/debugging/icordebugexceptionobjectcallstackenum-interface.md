---
description: '詳細については、次を参照してください: を参照してください。表示インターフェイス'
title: ICorDebugExceptionObjectCallStackEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
ms.openlocfilehash: c72f4299bf3ebc5de2d2ed196801d93ff5fe4356
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693357"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a>ICorDebugExceptionObjectCallStackEnum インターフェイス

例外オブジェクトに埋め込まれているコール スタックの情報の列挙子を提供します。 このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[いい Exceptionobjectcallstackenum:: Next](icordebugexceptionobjectcallstackenum-next-method.md)|例外オブジェクトの呼び出し履歴に関する情報を格納している、指定した数の [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) オブジェクトを取得します。|  
  
## <a name="remarks"></a>解説  

 `ICorDebugExceptionObjectCallStackEnum`インターフェイスは、ICorDebugEnum インターフェイスを実装します。  
  
 `ICorDebugExceptionObjectCallStackEnum` [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md)オブジェクトを使用してインスタンスに値を設定するには、 [EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)メソッドを呼び出します。 コレクション内のコールスタック項目を列挙するには、 [次](icordebugexceptionobjectcallstackenum-next-method.md) のように指定します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
