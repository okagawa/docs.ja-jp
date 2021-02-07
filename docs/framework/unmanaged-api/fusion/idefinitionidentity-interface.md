---
description: 詳細については、「IDefinitionIdentity インターフェイス」を参照してください。
title: IDefinitionIdentity インターフェイス
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
ms.openlocfilehash: 3471879cc822b655b786dd9d8234950cb4b99c1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760655"
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity インターフェイス

現在のスコープ内のアプリケーションを定義するコードの一意の署名を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|`IDefinitionIdentity` `IDefinitionIdentity` 指定した属性の変更を除き、このと同一の新しいオブジェクトへのインターフェイスポインターを取得します。|  
|`IDefinitionIdentity::EnumAttributes`|このに関連付けられている属性を格納している [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) オブジェクトへのインターフェイスポインターを取得し `IDefinitionIdentity` ます。|  
|`IDefinitionIdentity::GetAttribute`|指定した名前空間内の指定した名前の属性の値を取得します。|  
|`IDefinitionIdentity::SetAttribute`|指定した名前空間の指定した名前を持つ属性を、指定した値に設定します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** 分離 .h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
