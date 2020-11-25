---
title: USER_THREAD 構造体
ms.date: 03/30/2017
api_name:
- USER_THREAD
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- USER_THREAD
helpviewer_keywords:
- USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type:
- apiref
ms.openlocfilehash: 409651aa69e957418ad46f61e1bd57add0eb10a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722896"
---
# <a name="user_thread-structure"></a>USER_THREAD 構造体

スレッドに関する情報をデバッガーに提供します。 詳細については、 [INotifySource2:: SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) メソッドを参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`pSidBuffer`|スレッドバッファーのアドレス。|  
|`dwSidLen`|スレッドバッファーの長さ (バイト単位)。|  
|`dwTid`|スレッド ID。|  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** ProtocolNotify2  
  
## <a name="see-also"></a>関連項目

- [SetNotifyFilter メソッド](inotifysource2-setnotifyfilter-method.md)
- [シンボル ストア診断構造体](diagnostics-symbol-store-structures.md)
