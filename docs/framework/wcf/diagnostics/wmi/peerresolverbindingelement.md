---
description: 詳細については、「PeerResolverBindingElement」を参照してください。
title: PeerResolverBindingElement
ms.date: 03/30/2017
ms.assetid: 36882183-13a3-443f-8aae-62a7825d5633
ms.openlocfilehash: f3bb1b9e8c3acb94c1a3cf9eaa44c7ffeec07c51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803023"
---
# <a name="peerresolverbindingelement"></a>PeerResolverBindingElement

PeerResolverBindingElement  
  
## <a name="syntax"></a>構文  
  
```csharp
class PeerResolverBindingElement : BindingElement  
{  
  string ReferralPolicy;  
};  
```  
  
## <a name="methods"></a>メソッド  

 PeerResolverBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 PeerResolverBindingElement クラスには、次のプロパティがあります。  
  
### <a name="referralpolicy"></a>ReferralPolicy  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 ピア間で参照を共有する方法を指定します。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
