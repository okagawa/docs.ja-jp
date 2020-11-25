---
title: ICorDebugHeapEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
ms.openlocfilehash: 312052fcd683acbccb9ca616992bd635490aa2a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724365"
---
# <a name="icordebugheapenum-interface"></a>ICorDebugHeapEnum インターフェイス

マネージド ヒープのオブジェクトの列挙子を提供します。 このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Next メソッド](icordebugheapenum-next-method.md)|マネージヒープ上のオブジェクトに関する情報を格納している、指定した数の [COR_HEAPOBJECT](cor-heapobject-structure.md) インスタンスを取得します。|  
  
## <a name="remarks"></a>注釈  

 `ICorDebugHeapEnum`インターフェイスは、ICorDebugEnum インターフェイスを実装します。  
  
 `ICorDebugHeapEnum`インスタンスには、 [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md)メソッドを呼び出すことによって[COR_HEAPOBJECT](cor-heapobject-structure.md)インスタンスが設定されます。 コレクション内の各 [COR_HEAPOBJECT](cor-heapobject-structure.md) インスタンスは、ヒープ上のライブオブジェクト、またはオブジェクトではなく、ガベージコレクターによってまだ収集されていないオブジェクトを表します。 コレクション内の [COR_HEAPOBJECT](cor-heapobject-structure.md) オブジェクトを列挙するには、 [次](icordebugheapenum-next-method.md) のメソッドを使用します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
