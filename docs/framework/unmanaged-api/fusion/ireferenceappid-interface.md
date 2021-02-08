---
description: 詳細については、「IReferenceAppId インターフェイス」を参照してください。
title: IReferenceAppId インターフェイス
ms.date: 03/30/2017
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
ms.openlocfilehash: 66838d6ae66aa7de05d899e9fa980308718e2a38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800072"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId インターフェイス

現在のスコープ内のアプリケーションの一意の識別子への参照を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|このによって参照されるアプリケーションのコード識別子の文字列形式へのポインターを取得し `IReferenceAppId` ます。|  
|`IReferenceAppId::put_CodeBase`|このによって参照されるアプリケーションのコード識別子を設定し `IReferenceAppId` ます。|  
|`IReferenceAppId::EnumAppPath`|`IEnumReferenceIdentity`こののメンバーを表すインスタンスを格納しているインスタンスへのインターフェイスポインターを取得し `IReferenceIdentity` `IReferenceAppId` ます。|  
|`IReferenceAppId::get_SubscriptionId`|このに対するサブスクリプションのトークン識別子の文字列形式へのポインターを取得し `IReferenceAppId` ます。|  
|`IReferenceAppId::put_SubscriptionId`|サブスクリプションのトークン識別子を `IReferenceAppId` 指定された文字列値に設定します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** 分離 .h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
- [IEnumReferenceIdentity インターフェイス](ienumreferenceidentity-interface.md)
- [IReferenceIdentity インターフェイス](ireferenceidentity-interface.md)
