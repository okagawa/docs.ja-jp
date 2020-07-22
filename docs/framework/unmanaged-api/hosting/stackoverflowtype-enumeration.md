---
title: StackOverflowType 列挙型
ms.date: 03/30/2017
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
ms.openlocfilehash: f399d33dbe05cb5768aa45533ef30d28409e18e2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006468"
---
# <a name="stackoverflowtype-enumeration"></a>StackOverflowType 列挙型
スタックオーバーフローイベントの根底にある原因を示す値を格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`SO_ClrEngine`|スタックオーバーフローは、実行エンジンによって発生しました。|  
|`SO_Managed`|スタックオーバーフローは、マネージコードによって発生しました。|  
|`SO_Other`|スタックオーバーフローは、アンマネージコードによって発生しました。|  
  
## <a name="remarks"></a>コメント  
 この情報は、 [Iactiononclrevent:: OnEvent](iactiononclrevent-onevent-method.md)メソッドの呼び出しによってホストに渡されます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** Mscoree.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスティングの列挙型](hosting-enumerations.md)
