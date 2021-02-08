---
description: '詳細情報: StackTrace_SimpleContext 構造'
title: StackTrace_SimpleContext 構造体
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
ms.openlocfilehash: 22a0acada5ef2d392dfdef5326953be137280d7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800553"
---
# <a name="stacktrace_simplecontext-structure"></a>StackTrace_SimpleContext 構造体

完全な `CONTEXT` 構造の代わりに使用できる単純なコンテキストを提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`StackOffset`|スタックポインター、または x86 プラットフォームの enter スタックポインター (ESP)。|  
|`FrameOffset`|フレームオフセット、または x86 プラットフォームでの EBP レジスタ。|  
|`InstructionOffset`|命令ポインター、または x86 プラットフォームの enter 命令ポインター (EIP)。|  
  
## <a name="remarks"></a>解説  

 通常、スタックトレース関数はアドレス、フレームオフセット、およびスタックアドレスだけを返す必要があるため、必要に応じて、大きな構造体の代わりに構造体を使用することもでき `SimpleContext` `CONTEXT` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** SOS_Stacktrace  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
