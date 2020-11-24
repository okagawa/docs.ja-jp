---
title: CustomDumpItem 構造体
ms.date: 03/30/2017
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
ms.openlocfilehash: c77e93686c7d121e9fe2a92f03970404ab823dc0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673242"
---
# <a name="customdumpitem-structure"></a>CustomDumpItem 構造体

エラー報告のカスタムダンプに追加するアイテムについて説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`itemKind`|追加する項目の種類を示す [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) 値。|  
|`pReserved`|現在は使用しません。 共用体に追加された項目は、ポインターサイズ以下である必要があります。 `struct`が必要な場合は、それを個別に割り当てて、それをポイントする必要があります。|  
  
## <a name="remarks"></a>注釈  

 [ICLRErrorReportingManager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) は、型のパラメーターを受け取り `CustomDumpItem` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト構造体](hosting-structures.md)
