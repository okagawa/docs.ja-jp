---
title: HOST_TYPE 列挙型
ms.date: 03/30/2017
api_name:
- HOST_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- HOST_TYPE
helpviewer_keywords:
- HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type:
- apiref
ms.openlocfilehash: 31640ada28af8e35554b91d5931d427fbaa8dcbe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721856"
---
# <a name="host_type-enumeration"></a>HOST_TYPE 列挙型

アプリケーションを起動しているホストの種類を指定する値を格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|AppLaunch.exe からアプリケーションを起動します。<br /><br /> 部分的に信頼されたアプリケーションには、この値を使用します。|  
|`HOST_TYPE_CORFLAG`|アプリケーションを直接起動します。 つまり、アプリケーションを独自の .exe ファイルから起動します。<br /><br /> この値は、完全に信頼されたアプリケーションに使用します。|  
|`HOST_TYPE_DEFAULT`|HOST_TYPE_APPLAUNCH と同じです。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスティングの列挙型](hosting-enumerations.md)
