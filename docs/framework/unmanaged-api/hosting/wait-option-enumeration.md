---
description: '詳細情報: WAIT_OPTION 列挙型'
title: WAIT_OPTION 列挙型
ms.date: 03/30/2017
api_name:
- WAIT_OPTION
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAIT_OPTION
helpviewer_keywords:
- WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type:
- apiref
ms.openlocfilehash: 1d651909e0f62f2db7478a6e0b37139d1f953196
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679135"
---
# <a name="wait_option-enumeration"></a>WAIT_OPTION 列挙型

共通言語ランタイム (CLR) ブロックによって操作が要求された場合にホストが実行するアクションを示す値を格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|CLR が [IHostTask:: Alert](ihosttask-alert-method.md) メソッドを呼び出した場合に、タスクが起こされる必要があることをホストに通知します。|  
|`WAIT_MSGPUMP`|スレッドがブロックされた場合に、現在の OS スレッドでメッセージをポンプする必要があることをホストに通知します。 ランタイムは、スレッドに対してのみこの値を指定し <xref:System.Threading.ApartmentState.STA> ます。|  
|`WAIT_NOTINDEADLOCK`|指定された同期要求がホストによって壊れていないことをホストに通知します。 つまり、ホストはを返すことができません `HOST_E_DEADLOCK` 。|  
  
## <a name="remarks"></a>解説  

 [IHostTaskManager:: Sleep](ihosttaskmanager-sleep-method.md)メソッドと[IHostTaskManager:: switchtotask](ihosttaskmanager-switchtotask-method.md)メソッドは、どちらもこの型のパラメーターを受け取ります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスティングの列挙型](hosting-enumerations.md)
