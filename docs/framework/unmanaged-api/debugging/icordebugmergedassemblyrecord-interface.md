---
title: ICorDebugMergedAssemblyRecord インターフェイス
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: a26702c6b21e4bfe352d861387a80b976a8dc556
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710494"
---
# <a name="icordebugmergedassemblyrecord-interface"></a>ICorDebugMergedAssemblyRecord インターフェイス

マージされたアセンブリに関する情報を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetCulture メソッド](icordebugmergedassemblyrecord-getculture-method.md)|アセンブリのカルチャ名文字列を取得します。|  
|[GetIndex メソッド](icordebugmergedassemblyrecord-getindex-method.md)|アセンブリのプレフィックス インデックスを取得します。|  
|[GetPublicKey メソッド](icordebugmergedassemblyrecord-getpublickey-method.md)|アセンブリの公開キーを取得します。|  
|[GetPublicKeyToken メソッド](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|アセンブリの公開キー トークンを取得します。|  
|[GetSimpleName メソッド](icordebugmergedassemblyrecord-getsimplename-method.md)|アセンブリの簡易名を取得します。|  
|[GetVersion メソッド](icordebugmergedassemblyrecord-getversion-method.md)|アセンブリのバージョン情報を取得します。|  
  
## <a name="remarks"></a>注釈  
  
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
