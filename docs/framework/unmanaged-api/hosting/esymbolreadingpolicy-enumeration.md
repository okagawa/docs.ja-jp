---
title: ESymbolReadingPolicy 列挙型
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
ms.openlocfilehash: 42ce1f02294db98c5c593a5f16de5226703d5f9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733712"
---
# <a name="esymbolreadingpolicy-enumeration"></a>ESymbolReadingPolicy 列挙型

プログラムデータベース (PDB) ファイルを読み取るためのポリシーを設定する値が含まれます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`eSymbolReadingAlways`|デバッガーが常に PDB ファイルを読み取る必要があることを指定します。|  
|`eSymbolReadingFullTrustOnly`|デバッガーが、完全に信頼されたアセンブリに関連付けられている PDB ファイルのみを読み取るように指定します。|  
|`eSymbolReadingNever`|デバッガーが PDB ファイルを読み取らないように指定します。|  
  
## <a name="remarks"></a>注釈  

 `ESymbolReadingPolicy`列挙体は、 [ICLRDebugManager:: SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md)メソッドと共に使用されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスティングの列挙型](hosting-enumerations.md)
