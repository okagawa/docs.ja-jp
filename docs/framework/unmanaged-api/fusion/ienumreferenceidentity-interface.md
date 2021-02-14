---
description: 詳細については、「IEnumReferenceIdentity インターフェイス」を参照してください。
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
ms.openlocfilehash: a7f17793fd737b5153c27dae59fb2aa87b46cf48
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100465302"
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
