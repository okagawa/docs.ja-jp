---
title: SYMLINEDELTA 構造体
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
ms.openlocfilehash: dd45703540f8dc41b746ca03b4f09d74186aa9aa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690942"
---
# <a name="symlinedelta-structure"></a>SYMLINEDELTA 構造体

編集の結果として移動されたメソッドについて、シンボルハンドラーに情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`mdMethod`|メソッドのメタデータトークン。|  
|`delta`|メソッドが移動された行の数。|  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断構造体](diagnostics-symbol-store-structures.md)
