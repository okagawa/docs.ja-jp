---
title: ECustomDumpFlavor 列挙型
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
ms.openlocfilehash: 1b8440ed6e878aac3dd08d9f8ed528c93739a724
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686320"
---
# <a name="ecustomdumpflavor-enumeration"></a>ECustomDumpFlavor 列挙型

エラーを報告するときに、ヒープダンプのカスタムサブセットに含めるアイテムを示す値を格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|カスタムヒープダンプをミニダンプとして起動し、同じメソッドに渡される [Customdumpitem](customdumpitem-structure.md) インスタンスによって指定された追加データを含めるように指定します。|  
|`DUMP_FLAVOR_NonHeapCLRState`|カスタムヒープダンプで、動的に割り当てられていないすべての実行時状態データを収集するように指定します。|  
  
## <a name="remarks"></a>注釈  

 型のパラメーター `ECustomDumpFlavor` は、 [ICLRErrorReportingManager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) メソッドに渡されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ECustomDumpItemKind 列挙型](ecustomdumpitemkind-enumeration.md)
- [ICLRErrorReportingManager インターフェイス](iclrerrorreportingmanager-interface.md)
- [ホスティングの列挙型](hosting-enumerations.md)
