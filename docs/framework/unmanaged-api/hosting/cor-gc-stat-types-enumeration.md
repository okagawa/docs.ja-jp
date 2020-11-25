---
title: COR_GC_STAT_TYPES 列挙体
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
ms.openlocfilehash: c14e27b67fc600e2684f8c967af30bb9a5cee126
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716742"
---
# <a name="cor_gc_stat_types-enumeration"></a>COR_GC_STAT_TYPES 列挙体

ガベージコレクション用に記録する統計を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a>解説  

 この列挙体は、 [ICLRGCManager:: GetStats](iclrgcmanager-getstats-method.md)メソッドによって設定される[COR_GC_STATS](cor-gc-stats-structure.md)構造内の統計を指定します。  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_GC_COUNTS`|生成されるたびに実行されるガベージコレクションの数を記録します。|  
|`COR_GC_MEMORYUSAGE`|メモリ使用量とガベージコレクションサイズの統計情報を記録します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** GCHost、GCHost  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [COR_GC_STATS 構造体](cor-gc-stats-structure.md)
- [ホスティングの列挙型](hosting-enumerations.md)
