---
title: IDefinitionAppId インターフェイス
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
ms.openlocfilehash: 1e6c42d8e74d2d3e7925c657c67832f662416e64
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673866"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId インターフェイス

現在のスコープ内のアプリケーションを定義するコードの一意の識別子を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|このオブジェクトのコードを表す書式設定された文字列を取得し `IDefinitionAppId` ます。|  
|`IDefinitionAppId::put_Codebase`|このオブジェクトのコード `IDefinitionAppId` を、指定した書式設定された文字列値に設定します。|  
|`IDefinitionAppId::EnumAppPath`|現在のアプリケーションパス内のアセンブリを格納する [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) オブジェクトへのインターフェイスポインターを取得します。|  
|`IDefinitionAppId::SetAppPath`|現在のスコープ内のアセンブリのアプリケーションパスを、指定した [IDefinitionIdentity](idefinitionidentity-interface.md) オブジェクトによって参照される値に設定します。|  
|`IDefinitionAppId::get_SubscriptionId`|このオブジェクトに対するサブスクリプションのトークン識別子の文字列形式へのポインターを取得し `IDefinitionAppId` ます。|  
|`IDefinitionAppId::put_SubscriptionId`|このオブジェクトに対するサブスクリプションのトークン識別子 `IDefinitionAppId` を、指定された文字列値に設定します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** 分離 .h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
