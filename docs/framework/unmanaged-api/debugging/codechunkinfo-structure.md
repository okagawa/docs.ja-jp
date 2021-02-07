---
description: '詳細については、次を参照してください: CodeChunkInfo 構造体'
title: CodeChunkInfo 構造体
ms.date: 03/30/2017
api_name:
- CodeChunkInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CodeChunkInfo
helpviewer_keywords:
- CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type:
- apiref
ms.openlocfilehash: 017a9ee8c608d4efae98eb0a342a3371ef8ec310
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712351"
---
# <a name="codechunkinfo-structure"></a>CodeChunkInfo 構造体

メモリ内のコードの単一のチャンクを表しています。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`startAddr`|`CORDB_ADDRESS`チャンクの開始アドレスを示す値です。|  
|`length`|チャンクのサイズ (バイト単位)。|  
  
## <a name="remarks"></a>解説  

 コードの1つのチャンクは、関数などのコードオブジェクトの一部であるネイティブコードの領域です。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug .idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetCodeChunks メソッド](icordebugcode2-getcodechunks-method.md)
- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
