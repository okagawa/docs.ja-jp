---
description: '詳細情報: テキスト枠インターフェイス'
title: ICorDebugFrame インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
ms.openlocfilehash: d0fd629672d535f89fe78c178032937443d9dfbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692850"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame インターフェイス

現在のスタックのフレームを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateStepper メソッド](icordebugframe-createstepper-method.md)|このに対して相対的なステップ実行操作を実行する ICorDebugStepper を取得し `ICorDebugFrame` ます。|  
|[GetCallee メソッド](icordebugframe-getcallee-method.md)|このフレームが呼び出された現在のチェーン内のへのポインターを取得し `ICorDebugFrame` ます。または、このがチェーン内の最も内側のフレームである場合は null を返します。|  
|[GetCaller メソッド](icordebugframe-getcaller-method.md)|このフレームを呼び出した現在のチェーン内のへのポインターを取得し `ICorDebugFrame` ます。これがチェーンの最も外側のフレームである場合は null を返します。|  
|[GetChain メソッド](icordebugframe-getchain-method.md)|このが含まれている、ツールチェーンへのポインターを取得し `ICorDebugFrame` ます。|  
|[GetCode メソッド](icordebugframe-getcode-method.md)|このスタックフレームに関連付けられているテキストコードへのポインターを取得します。|  
|[GetFunction メソッド](icordebugframe-getfunction-method.md)|このスタックフレームに関連付けられているコードを格納しているコードを指すポインターを取得します。|  
|[GetFunctionToken メソッド](icordebugframe-getfunctiontoken-method.md)|このスタックフレームに関連付けられているコードを含む関数のメタデータトークンを取得します。|  
|[GetStackRange メソッド](icordebugframe-getstackrange-method.md)|このによって表されるスタックフレームの絶対アドレス範囲を取得し `ICorDebugFrame` ます。|  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
