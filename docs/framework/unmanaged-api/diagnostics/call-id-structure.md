---
title: CALL_ID 構造体
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
ms.openlocfilehash: 3f41dd969e25f7a42308ff0b7b2d617344284b38
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725249"
---
# <a name="call_id-structure"></a>CALL_ID 構造体

呼び出されている関数についての情報をデバッガーに提供します。 詳細については、 [INotifySink2](inotifysink2-interface.md) インターフェイスを参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`szMachine`|呼び出しを行っているコンピューターを識別します。|  
|`dwPid`|マシンプロセッサを識別します。|  
|`pUserThread`|呼び出しを実行しているスレッドを識別します。|  
|`addrStackPointer`|呼び出し履歴のアドレスを指定します。|  
|`szEntryPoint`|呼び出しのアドレスを指定します。|  
|`szDestinationMachine`|呼び出しを実行するコンピューターを識別します。|  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** ProtocolNotify2  
  
## <a name="see-also"></a>関連項目

- [INotifySink2 インターフェイス](inotifysink2-interface.md)
- [シンボル ストア診断構造体](diagnostics-symbol-store-structures.md)
