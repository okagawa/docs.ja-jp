---
description: '詳細情報: ICorDebugValue インターフェイス'
title: ICorDebugValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
ms.openlocfilehash: cae8fdef5c1c49cbabc25d3d547cb5748a9eeee1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690312"
---
# <a name="icordebugvalue-interface"></a>ICorDebugValue インターフェイス

デバッグ中のプロセスの値を表します。 値には、読み取りまたは書き込みの値を指定できます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateBreakpoint メソッド](icordebugvalue-createbreakpoint-method.md)|このメソッドは、現在実装されていません。|  
|[GetAddress メソッド](icordebugvalue-getaddress-method.md)|このオブジェクトのアドレスを取得します。このアドレスは、 `ICorDebugValue` デバッグ中のプロセスです。|  
|[GetSize メソッド](icordebugvalue-getsize-method.md)|このオブジェクトのサイズ (バイト単位) を取得し `ICorDebugValue` ます。|  
|[GetType メソッド](icordebugvalue-gettype-method.md)|このオブジェクトのプリミティブ型を取得し `ICorDebugValue` ます。|  
  
## <a name="remarks"></a>解説  

 一般に、値オブジェクトの所有権は、返されるときに渡されます。 オブジェクトの終了時に、オブジェクトからの参照を削除するのは、受信者の責任です。  
  
 値が取得された場所によっては、プロセスが再開された後も値が有効なままにならないことがあります。 そのため、一般に、次のように、値は、は、「いいね [:: Continue](icordebugcontroller-continue-method.md) メソッドの呼び出し」で保持するべきではありません。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugValue3 インターフェイス](icordebugvalue3-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
