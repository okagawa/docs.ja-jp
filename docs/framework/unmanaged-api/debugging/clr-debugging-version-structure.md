---
description: '詳細情報: CLR_DEBUGGING_VERSION 構造'
title: CLR_DEBUGGING_VERSION 構造体
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
ms.openlocfilehash: 2d274a91948b98dc309cd5670c3dd3bf6cd01e2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772784"
---
# <a name="clr_debugging_version-structure"></a>CLR_DEBUGGING_VERSION 構造体

デバッグのために共通言語ランタイム (CLR) の製品バージョンを定義します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`wStructVersion`|構造体のバージョン番号|  
|`wMajor`|メジャー バージョン番号。|  
|`wMinor`|マイナー バージョン番号。|  
|`wBuild`|ビルド番号。|  
|`wRevision`|リビジョン番号。|  
  
## <a name="remarks"></a>解説  

 構造体 `CLR_DEBUGGING_VERSION` は COR_VERSION 構造体と同じですが、構造体には `CLR_DEBUGGING_VERSION` 追加の構造体のバージョンフィールド () が用意されて `wStructVersion` います。 現在、このフィールドは0に設定する必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug .idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
