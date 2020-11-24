---
title: ICorDebugVirtualUnwinder インターフェイス
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 67f2234d37165e421874815bdc2ef34f8f50749a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679378"
---
# <a name="icordebugvirtualunwinder-interface"></a>ICorDebugVirtualUnwinder インターフェイス

スタック アンワインドを支援するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|名前|  
|------------|----------|  
|[GetContext メソッド](icordebugvirtualunwinder-getcontext-method.md)|このアンワインダーの現在のコンテキストを取得します。|  
|[Next メソッド](icordebugvirtualunwinder-next-method.md)|呼び出し元のコンテキストに進みます。|  
  
## <a name="remarks"></a>注釈  

 スタック アンワインドを支援するため、`ICorDebugVirtualUnwinder` インターフェイスのメンバーがデバッガーにより実装されます。  
  
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
