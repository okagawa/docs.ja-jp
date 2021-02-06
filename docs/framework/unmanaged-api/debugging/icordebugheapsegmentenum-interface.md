---
description: 詳細については、「ICorDebugHeapSegmentEnum インターフェイス」を参照してください。
title: ICorDebugHeapSegmentEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
ms.openlocfilehash: 614bae0ea5e3eb7816fdeec23a0dc7aa6e44801d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660883"
---
# <a name="icordebugheapsegmentenum-interface"></a>ICorDebugHeapSegmentEnum インターフェイス

マネージド ヒープのメモリ領域の列挙子を提供します。 このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[次のメソッド](icordebugheapsegmentenum-next-method.md)|マネージヒープの領域に関する情報を格納している、指定した数の [COR_SEGMENT](cor-segment-structure.md) インスタンスを取得します。|  
  
## <a name="remarks"></a>解説  

 `ICorDebugHeapSegmentEnum`インターフェイスは、ICorDebugEnum インターフェイスを実装します。  
  
 `ICorDebugHeapSegmentEnum`インスタンスには、 [ICorDebugProcess5:: EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md)メソッドを呼び出すことによって[COR_SEGMENT](cor-segment-structure.md)インスタンスが設定されます。 コレクション内の [COR_SEGMENT](cor-segment-structure.md) オブジェクトは、 [ICorDebugHeapSegmentEnum:: Next](icordebugheapsegmentenum-next-method.md) メソッドを呼び出すことによって列挙できます。  
  
 `ICorDebugHeapSegmentEnum`コレクションオブジェクトは、マネージオブジェクトを含む可能性があるすべてのメモリ領域を列挙しますが、それらの領域にマネージオブジェクトが実際に存在することを保証するわけではありません。 これには、空または予約済みのメモリ領域に関する情報が含まれる場合があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
