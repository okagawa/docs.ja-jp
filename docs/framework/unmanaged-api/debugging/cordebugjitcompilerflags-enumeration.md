---
description: '詳細については、次を参照してください: CorDebugJITCompilerFlags 列挙型'
title: CorDebugJITCompilerFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlags
helpviewer_keywords:
- CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type:
- apiref
ms.openlocfilehash: 7e5337293aa4fe446deb12653acd22864eb7679a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801606"
---
# <a name="cordebugjitcompilerflags-enumeration"></a>CorDebugJITCompilerFlags 列挙型

マネージド Just-In-Time (JIT) コンパイラの動作に影響を与える値が含まれます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|コンパイラがコンパイルデータを追跡し、最適化を許可することを指定します。|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|コンパイラがコンパイルデータを追跡する必要があるが、最適化を無効にすることを指定します。|  
|`CORDEBUG_JIT_ENABLE_ENC`|コンパイラがコンパイルデータを追跡し、最適化を無効にして、エディットコンティニュテクノロジを有効にする必要があることを指定します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のデバッグ](debugging-enumerations.md)
