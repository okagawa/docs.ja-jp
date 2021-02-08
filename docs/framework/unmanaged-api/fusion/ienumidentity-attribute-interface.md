---
description: 詳細については、「IEnumIDENTITY_ATTRIBUTE インターフェイス」を参照してください。
title: IEnumIDENTITY_ATTRIBUTE インターフェイス
ms.date: 03/30/2017
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
ms.openlocfilehash: b621a722e35d5b31f487e8823b1627fdfe1e7888
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800150"
---
# <a name="ienumidentity_attribute-interface"></a>IEnumIDENTITY_ATTRIBUTE インターフェイス

現在のスコープ内のコードオブジェクトの属性の列挙子として機能します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|このと同じメンバーを含む新しいへのインターフェイスポインターを取得し `IEnumIDENTITY_ATTRIBUTE` `IEnumIDENTITY_ATTRIBUTE` ます。|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|このの要素に格納されているデータ `IEnumIDENTITY_ATTRIBUTE` を、指定したデータバッファーに書き込みます。|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|指定した数の属性を、現在の位置から開始して取得します。|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|命令ポインターをこのの先頭に移動し `IEnumIDENTITY_ATTRIBUTE` ます。|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|現在位置を開始位置として、指定した要素数だけ前方に命令ポインターを移動します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** 分離 .h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
