---
description: 詳細については、「ICorDebugLoadedModule インターフェイス」を参照してください。
title: ICorDebugLoadedModule インターフェイス
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: 6a1b466a9d2d7781fad7ac2bc8c24f0b2a5c23e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801229"
---
# <a name="icordebugloadedmodule-interface"></a>ICorDebugLoadedModule インターフェイス

読み込まれたモジュールについての情報を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetBaseAddress メソッド](icordebugloadedmodule-getbaseaddress-method.md)|読み込まれたモジュールのベース アドレスを取得します。|  
|[GetName メソッド](icordebugloadedmodule-getname-method.md)|読み込まれたモジュールの名前を取得します。|  
|[GetSize メソッド](icordebugloadedmodule-getsize-method.md)|読み込まれたモジュールのサイズ (バイト単位) を取得します。|  
  
## <a name="remarks"></a>解説  

 `ICorDebugLoadedModule` インターフェイスはデバッガーによって実装され、CLR デバッグ インターフェイスが、デバッガーから読み込まれたモジュールに関する情報を取得するために使用します。  
  
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
