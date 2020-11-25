---
title: IEnumReferenceIdentity インターフェイス
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
ms.openlocfilehash: bea357fe9a154ffb8f69228c7332c026dc2759e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728974"
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity インターフェイス

オブジェクトのコレクションの列挙子として機能し `IReferenceIdentity` ます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|このと同じメンバーを含む新しいへのインターフェイスポインターを取得し `IEnumReferenceIdentity` `IEnumReferenceIdentity` ます。|  
|`IEnumReferenceIdentity::Next`|現在の位置から開始して、指定した数の `IReferenceIdentity` オブジェクトを取得します。|  
|`IEnumReferenceIdentity::Reset`|命令ポインターをこのの先頭に移動し `IEnumReferenceIdentity` ます。|  
|`IEnumReferenceIdentity::Skip`|現在位置を開始位置として、指定した要素数だけ前方に命令ポインターを移動します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** 分離 .h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
- [IReferenceIdentity インターフェイス](ireferenceidentity-interface.md)
