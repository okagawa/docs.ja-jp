---
description: '詳細情報: COR_PRF_MISC 列挙型'
title: COR_PRF_MISC 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_MISC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MISC
helpviewer_keywords:
- COR_PRF_MISC enumeration [.NET Framework profiling]
ms.assetid: 619bb5de-e309-48b6-a3af-32d935a0ff46
topic_type:
- apiref
ms.openlocfilehash: 037ea040dfdf9f5be48369ab4d8e94b12aea51ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687598"
---
# <a name="cor_prf_misc-enumeration"></a>COR_PRF_MISC 列挙型

特殊な識別子を指定する定数値を含めます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|アセンブリにまだアタッチされていないモジュールに対して [ICorProfilerInfo:: GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md) によって使用される既定の識別子。|  
|`PROFILER_GLOBAL_CLASS`|クラスに属していないグローバル定数の既定のクラス識別子。|  
|`PROFILER_GLOBAL_MODULE`|モジュールに属さないグローバルオブジェクトの既定のモジュール識別子。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のプロファイリング](profiling-enumerations.md)
