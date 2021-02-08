---
description: '詳細情報: COR_GC_REFERENCE 構造'
title: COR_GC_REFERENCE 構造体
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
ms.openlocfilehash: 38518bb1eb870081621bf32af9e63cdaa208dbd3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801814"
---
# <a name="cor_gc_reference-structure"></a>COR_GC_REFERENCE 構造体

ガベージ コレクトされるオブジェクトに関する情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`domain`|ハンドルまたはオブジェクトが属するアプリケーションドメインへのポインター。 この値は、の場合もあり `null` ます。|  
|`location`|ガベージコレクションされるオブジェクトに対応する ICorDebugValue またはの値のインターフェイス。|  
|`type`|ルートの取得元を示す [Corgcreの Encetype](corgcreferencetype-enumeration.md) 列挙値。 詳細については、「解説」を参照してください。|  
|`extraData`|ガベージコレクションされるオブジェクトに関する追加データ。 この情報は、フィールドに示されているように、オブジェクトのソースによって異なり `type` ます。 詳細については、「解説」を参照してください。|  
  
## <a name="remarks"></a>解説  

 `type`フィールドは、参照の取得元を示す[Corgcreの型](corgcreferencetype-enumeration.md)の列挙値です。 特定の `COR_GC_REFERENCE` 値には、次のいずれかの種類のマネージオブジェクトを反映できます。  
  
- すべてのマネージスタックのオブジェクト ( `CorGCReferenceType.CorReferenceStack` )。 これには、マネージコードのライブ参照や、共通言語ランタイムによって作成されたオブジェクトが含まれます。  
  
- ハンドルテーブルからのオブジェクト ( `CorGCReferenceType.CorHandle*` )。 これには、モジュール内の厳密な参照 ( `HNDTYPE_STRONG` および `HNDTYPE_REFCOUNT` ) と静的変数が含まれます。  
  
- ファイナライザーキュー () からのオブジェクト `CorGCReferenceType.CorReferenceFinalizer` 。 ファイナライザーが実行されるまで、ファイナライザーはオブジェクトをキューに置いています。  
  
 フィールドには、 `extraData` 参照のソース (または型) に応じて追加のデータが含まれます。 次のいずれかの値になります。  
  
- `DependentSource`. がの `type` 場合 `CorGCREferenceType.CorHandleStrongDependent` 、このフィールドはオブジェクトであり、alive の場合、ガベージコレクトされるオブジェクトがルートになり `COR_GC_REFERENCE.Location` ます。  
  
- `RefCount`. がの `type` 場合 `CorGCREferenceType.CorHandleStrongRefCount` 、このフィールドはハンドルの参照カウントです。  
  
- `Size`. がの `type` 場合 `CorGCREferenceType.CorHandleStrongSizedByref` 、このフィールドはガベージコレクターによってオブジェクトのルートが計算されたオブジェクトツリーの最後のサイズになります。 この計算は必ずしも最新の状態ではないことに注意してください。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
