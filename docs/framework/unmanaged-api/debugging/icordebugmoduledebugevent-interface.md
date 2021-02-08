---
description: '詳細情報: モジュールの詳細'
title: ICorDebugModuleDebugEvent インターフェイス
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: 0c2d43d7b04caeea0407ede23f0df6e278d60c92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801034"
---
# <a name="icordebugmoduledebugevent-interface"></a>ICorDebugModuleDebugEvent インターフェイス

モジュールレベルのイベントをサポートするように、のモジュールレベル [のイベントを](icordebugdebugevent-interface.md) 拡張します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetModule メソッド](icordebugmoduledebugevent-getmodule-method.md)|ロードまたはアンロードされたばかりのマージ モジュールを取得します。|  
  
## <a name="remarks"></a>解説  

 [MODULE_LOADED](cordebugdebugeventkind-enumeration.md)イベントと[MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md)イベントの種類は、このインターフェイスを実装します。  
  
> [!NOTE]
> このインターフェイスは .NET ネイティブでのみ使用可能です。 インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
