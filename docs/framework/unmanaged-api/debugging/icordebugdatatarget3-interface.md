---
description: 詳細については、「ICorDebugDataTarget3 インターフェイス」を参照してください。
title: ICorDebugDataTarget3 インターフェイス
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: fa786b920d1a2e72dc2a7918e0514773862a0e85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710440"
---
# <a name="icordebugdatatarget3-interface"></a>ICorDebugDataTarget3 インターフェイス

提供され [たモジュール](icordebugdatatarget-interface.md) に関する情報を提供するために、によって、参照インターフェイスを論理的に拡張します。  
  
## <a name="method"></a>Method  
  
|Method|説明|  
|------------|-----------------|  
|[GetLoadedModules メソッド](icordebugdatatarget3-getloadedmodules-method.md)|これまでに読み込まれたモジュールの一覧を取得します。|  
  
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
