---
title: COR_HEAPOBJECT 構造体
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
ms.openlocfilehash: 54af02b48dabdf2042763954805f0d454323ac89
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726367"
---
# <a name="cor_heapobject-structure"></a>COR_HEAPOBJECT 構造体

マネージド ヒープ上のオブジェクトに関する情報が提供されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;
    ULONG64 size;
    COR_TYPEID type;
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`address`|メモリ内のオブジェクトのアドレス。|  
|`size`|オブジェクトの合計サイズ (バイト単位)。|  
|`type`|オブジェクトの型を表す [COR_TYPEID](cor-typeid-structure.md) トークン。|  
  
## <a name="remarks"></a>注釈  

 `COR_HEAPOBJECT`インスタンスを取得するには、 [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md)メソッドを呼び出すことによって設定される、表示されている[heapheapenum](icordebugheapenum-interface.md)インターフェイスオブジェクトを列挙します。  
  
 インスタンスは、 `COR_HEAPOBJECT` マネージヒープ上のライブオブジェクトに関する情報、またはオブジェクトではなく、ガベージコレクターによってまだ収集されていないオブジェクトに関する情報を提供します。  
  
 パフォーマンスを向上させるために、この `COR_HEAPOBJECT.address` フィールドは `CORDB_ADDRESS` デバッグ API の多くで使用される ICorDebugValue インターフェイス値ではなく、値になります。 指定されたオブジェクトアドレスの ICorDebugValue オブジェクトを取得するには、 `CORDB_ADDRESS` [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) メソッドに値を渡すことができます。  
  
 パフォーマンスを向上させるために、この `COR_HEAPOBJECT.type` フィールドは、 `COR_TYPEID` デバッグ API の多くで使用されている、テキスト型のインターフェイス値ではなく、値です。 指定された型 ID の `COR_TYPEID` [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) メソッドに値を渡すことができます。  
  
 構造体には、 `COR_HEAPOBJECT` 参照カウントの COM インターフェイスが含まれています。 のインスタンスを列挙子から取得する場合は、次の `COR_HEAPOBJECT` メソッドを呼び出す必要があります。その後、参照を解放する必要があります。 [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md)  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
