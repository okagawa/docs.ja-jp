---
description: 詳細については、「LogSwitchCallReason 列挙型」を参照してください。
title: LogSwitchCallReason 列挙型
ms.date: 03/30/2017
api_name:
- LogSwitchCallReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LogSwitchCallReason
helpviewer_keywords:
- LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type:
- apiref
ms.openlocfilehash: 46c457ee4c12fe9a73796aa7b7a5f599d90c9c6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800612"
---
# <a name="logswitchcallreason-enumeration"></a>LogSwitchCallReason 列挙型

デバッグとトレースの切り替えで実行された操作を示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`SWITCH_CREATE`|デバッグ/トレーススイッチが作成されました。|  
|`SWITCH_MODIFY`|デバッグ/トレーススイッチが変更されました。|  
|`SWITCH_DELETE`|デバッグ/トレーススイッチが削除されました。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のデバッグ](debugging-enumerations.md)
