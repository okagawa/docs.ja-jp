---
title: ETaskType 列挙型
ms.date: 03/30/2017
api_name:
- ETaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ETaskType
helpviewer_keywords:
- ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type:
- apiref
ms.openlocfilehash: 0fa72568df77c4916a3c6676e1dcca7c0c616c4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493319"
---
# <a name="etasktype-enumeration"></a>ETaskType 列挙型
[ICLRTask](iclrtask-interface.md)または[IHostTask](ihosttask-interface.md)インターフェイスによって表されるタスクの種類を示す値を格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`TT_ADUNLOAD`|インターフェイスは、アプリケーションドメインのアンロードタスクを表します。|  
|`TT_DEBUGGERHELPER`|インターフェイスは、デバッガーヘルパータスクを表します。|  
|`TT_FINALIZER`|インターフェイスは、ファイナライザータスクを表します。|  
|`TT_GC`|インターフェイスは、ガベージコレクションタスクを表します。|  
|`TT_THREADPOOL_GATE`|インターフェイスは、ゲートスレッドタスクを表します。|  
|`TT_THREADPOOL_IOCOMPLETION`|インターフェイスは、i/o スレッドタスクまたは完了ポートスレッドタスクを表します。|  
|`TT_THREADPOOL_TIMER`|インターフェイスは、タイマースレッドタスクを表します。|  
|`TT_THREADPOOL_WAIT`|インターフェイスは、待機スレッドタスクを表します。|  
|`TT_THREADPOOL_WORKER`|インターフェイスは、ワーカースレッドタスクを表します。|  
|`TT_UNKNOWN`|タスクは不明です。|  
|`TT_USER`|インターフェイスは、ユーザータスクを表します。|  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** Mscoree.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスティングの列挙型](hosting-enumerations.md)
