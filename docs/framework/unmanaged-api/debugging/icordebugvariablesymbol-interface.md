---
description: 詳細については、「ICorDebugVariableSymbol インターフェイス」を参照してください。
title: ICorDebugVariableSymbol インターフェイス
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: fa3fc1f318627e9175a3066c3bd3eac00929ea60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790543"
---
# <a name="icordebugvariablesymbol-interface"></a>ICorDebugVariableSymbol インターフェイス

変数のデバッグ シンボル情報を取得します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetName メソッド](icordebugvariablesymbol-getname-method.md)|変数の名前を取得します。|  
|[GetSize メソッド](icordebugvariablesymbol-getsize-method.md)|変数のサイズ (バイト単位) を取得します。|  
|[GetSlotIndex メソッド](icordebugvariablesymbol-getslotindex-method.md)|ローカル変数のマネージド スロット インデックスを取得します。|  
|[GetValue メソッド](icordebugvariablesymbol-getvalue-method.md)|変数の値をバイト配列として取得します。|  
|[SetValue メソッド](icordebugvariablesymbol-setvalue-method.md)|バイト配列の値を変数に代入します。|  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このインターフェイスは .NET ネイティブでのみ使用可能です。 .NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
