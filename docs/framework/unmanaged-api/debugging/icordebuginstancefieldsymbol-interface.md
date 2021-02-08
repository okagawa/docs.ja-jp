---
description: '詳細については、次の情報を参照してください: いいでしょう。シンボルインターフェイス'
title: ICorDebugInstanceFieldSymbol インターフェイス
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: aa47c858ec5b4b0d04b851357fe81c0fc9b2e30a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791133"
---
# <a name="icordebuginstancefieldsymbol-interface"></a>ICorDebugInstanceFieldSymbol インターフェイス

インスタンス フィールドのデバッグ シンボル情報を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetName メソッド](icordebuginstancefieldsymbol-getname-method.md)|インスタンス フィールドの名前を取得します。|  
|[GetOffset メソッド](icordebuginstancefieldsymbol-getoffset-method.md)|このインスタンス フィールドの親クラスにおける、このインスタンス フィールドのオフセット (バイト単位) を取得します。|  
|[GetSize メソッド](icordebuginstancefieldsymbol-getsize-method.md)|インスタンス フィールドのサイズ (バイト単位) を取得します。|  
  
## <a name="remarks"></a>解説  

 `ICorDebugInstanceFieldSymbol` インターフェイスは、インスタンス フィールドのデバッグ シンボル情報を取得するために使用されます。  
  
> [!NOTE]
> このインターフェイスは .NET ネイティブでのみ使用可能です。 .NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugStaticFieldSymbol インターフェイス](icordebugstaticfieldsymbol-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
