---
title: ICorDebugILCode2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
ms.openlocfilehash: b9289b5afc88c926ce585a4e620364cf2dc979d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703331"
---
# <a name="icordebugilcode2-interface"></a>ICorDebugILCode2 インターフェイス

[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 では、この [コード](icordebugilcode-interface.md) インターフェイスを論理的に拡張して、関数のローカル変数シグネチャのトークンを返すメソッドを提供し、プロファイラーのインストルメント化された中間言語 (il) オフセットを元のメソッドの il オフセットにマップします。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetInstrumentedILMap メソッド](icordebugilcode2-getinstrumentedilmap-method.md)|プロファイラーのインストルメント化された IL オフセットから、このインスタンスに対する元のメソッドの IL オフセットへのマップを返します。|  
|[GetLocalVarSigToken メソッド](icordebugilcode2-getlocalvarsigtoken-method.md)|このインスタンスで示される関数について、ローカル変数のシグネチャのメタデータ トークンを取得します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugILCode インターフェイス](icordebugilcode-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
