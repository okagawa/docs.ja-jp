---
title: CorDebugUnmappedStop 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
ms.openlocfilehash: e251bf67adcaf2bbd6565eda068d487eb0d70efd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725774"
---
# <a name="cordebugunmappedstop-enumeration"></a>CorDebugUnmappedStop 列挙型

ステッパによるコード実行の停止をトリガーする可能性のあるマップ解除したコードの型を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`STOP_NONE`|どの種類のマップされていないコードでも停止しないでください。|  
|`STOP_PROLOG`|プロローグコードで停止します。|  
|`STOP_EPILOG`|エピローグコードで停止します。|  
|`STOP_NO_MAPPING_INFO`|マッピング情報のないコードで停止します。|  
|`STOP_OTHER_UNMAPPED`|プロローグ、エピローグ、非マッピング情報、またはアンマネージカテゴリに適合しない、マップされていないコードで停止します。|  
|`STOP_UNMANAGED`|アンマネージコードで停止します。 この値は、相互運用機能デバッグでのみ有効です。|  
|`STOP_ALL`|すべての種類のマップされていないコードで停止します。|  
  
## <a name="remarks"></a>注釈  

 [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md)メソッドを使用して、ステッパが停止するマップされていないコードを指定するフラグを設定します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のデバッグ](debugging-enumerations.md)
