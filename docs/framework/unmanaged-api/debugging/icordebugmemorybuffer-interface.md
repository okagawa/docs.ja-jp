---
description: '詳細については、次を参照してください: いい Memorybuffer インターフェイス'
title: ICorDebugMemoryBuffer インターフェイス
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: 94eeb0f31c0e1c053fabbd556768fa65dda2d328
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754018"
---
# <a name="icordebugmemorybuffer-interface"></a>ICorDebugMemoryBuffer インターフェイス

メモリ内のバッファーを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetSize メソッド](icordebugmemorybuffer-getsize-method.md)|メモリ バッファーのサイズ (バイト単位) を取得します。|  
|[GetStartAddress メソッド](icordebugmemorybuffer-getstartaddress-method.md)|メモリ バッファーの開始アドレスを取得します。|  
  
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
