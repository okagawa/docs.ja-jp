---
description: '詳細については、次のページを参照してください: を参照'
title: ICorDebugExceptionDebugEvent::GetNativeIP メソッド
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: 89bda36efc59e2462634c3d8a3a5835c9d4b3354
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693461"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a>ICorDebugExceptionDebugEvent::GetNativeIP メソッド

この例外デバッグ イベントのネイティブ命令ポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pIP`  
 [out] この例外デバッグ イベントのネイティブ命令ポインターに対するポインター。 詳細については、次の「解説」を参照してください。  
  
## <a name="remarks"></a>解説  

 この命令ポインターの意味は、次の表に示すように、イベントの種類によって異なります。  
  
|イベントの種類|`pStackPointer` 値の意味|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|障害の発生した命令のアドレス。|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|例外が発生しなかった場合に実行が再開される、 [Getstackpointer](icordebugexceptiondebugevent-getstackpointer-method.md) メソッドによって示されるフレーム内のコードアドレス。 例外によって、`try/catch/finally` 句の catch ブロックなどの別のコードがこのフレーム内で実行される原因となることもあれば、そうでない場合もあります。|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](cordebugrecordformat-enumeration.md)|`catch` [Getstackpointer](icordebugexceptiondebugevent-getstackpointer-method.md)メソッドによって示されるフレーム内でハンドラーの実行が開始されるコードアドレス。|  
|[MANAGED_EXCEPTION_UNHANDLED](cordebugrecordformat-enumeration.md)|`pIP` が 0 です。|  
  
 イベントの種類は、[テキスト形式の [イベント:: GetEventKind](icordebugdebugevent-geteventkind-method.md) メソッドから取得できます。  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugExceptionDebugEvent インターフェイス](icordebugexceptiondebugevent-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
