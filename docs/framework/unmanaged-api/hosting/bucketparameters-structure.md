---
description: '詳細については、次を参照してください: BucketParameters 構造体'
title: BucketParameters 構造体
ms.date: 03/30/2017
api_name:
- BucketParameters
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- BucketParameters
helpviewer_keywords:
- BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type:
- apiref
ms.openlocfilehash: e2d701caa0e2374cb6b44d5fb5537f2ecc7e34fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799968"
---
# <a name="bucketparameters-structure"></a>BucketParameters 構造体

イベントの型名と、イベントに関連付けられている現在の例外のパラメーターを格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;
    WCHAR pszEventTypeName[255];
    WCHAR pszParams[10][255];
} BucketParameters;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`fInited`|`true`この構造体の残りの部分が有効な場合は。それ以外の場合は `false` 。|  
|`pszEventTypeName`|イベントの種類の名前。|  
|`pszParams`|文字列の配列。各文字列は、イベントに関連付けられている現在の例外のパラメーターを指定します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト構造体](hosting-structures.md)
