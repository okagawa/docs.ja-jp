---
title: COR_TYPE_LAYOUT 構造体
ms.date: 03/30/2017
api_name:
- COR_TYPE_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPE_LAYOUT
helpviewer_keywords:
- COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type:
- apiref
ms.openlocfilehash: f33c8f5cf218979404063342d9b1cc5123839f83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726328"
---
# <a name="cor_type_layout-structure"></a>COR_TYPE_LAYOUT 構造体

メモリ内のオブジェクトのレイアウトに関する情報が提供されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`parentID`|この型への親の型の識別子。 型 id がに対応する場合、これは NULL 型 id (token1 = 0, token2 = 0) になり <xref:System.Object?displayProperty=nameWithType> ます。|  
|`objectSize`|この型のオブジェクトの基本サイズ。 これは、変数サイズが設定されていないオブジェクトの合計サイズです。|  
|`numFields`|この型のオブジェクトに含まれるフィールドの数。|  
|`boxOffset`|この型がボックス化されている場合は、オブジェクトのフィールドの開始オフセット。 このフィールドは、プリミティブや構造体などの値型に対してのみ有効です。|  
|`type`|この型が属する CorElementType。|  
  
## <a name="remarks"></a>注釈  

 `numFields`が0より大きい場合は、 [ICorDebugProcess5:: GetTypeFields](icordebugprocess5-gettypefields-method.md)メソッドを呼び出して、この型のフィールドに関する情報を取得できます。 `type`が `ELEMENT_TYPE_STRING` 、 `ELEMENT_TYPE_ARRAY` 、またはの場合 `ELEMENT_TYPE_SZARRAY` 、この型のオブジェクトのサイズは可変になり、 [COR_TYPEID](cor-typeid-structure.md)構造体を[ICorDebugProcess5:: getarraylayout](icordebugprocess5-getarraylayout-method.md)メソッドに渡すことができます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
