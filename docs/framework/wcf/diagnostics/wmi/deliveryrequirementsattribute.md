---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: a70a4ba40b569acc7893b21d796194224dc4ee78
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274050"
---
# <a name="deliveryrequirementsattribute"></a>DeliveryRequirementsAttribute

DeliveryRequirementsAttribute  
  
## <a name="syntax"></a>構文  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a>メソッド  

 DeliveryRequirementsAttribute クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 DeliveryRequirementsAttribute クラスには、次のプロパティがあります。  
  
### <a name="queueddeliveryrequirements"></a>QueuedDeliveryRequirements  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 サービスのバインドがコントラクトをサポートするかどうかを指定します。  
  
### <a name="requireordereddelivery"></a>RequireOrderedDelivery  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 バインディングが順序付きメッセージをサポートするかどうかを指定します。  
  
### <a name="targetcontract"></a>TargetContract  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 適用先となるコントラクトです。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>
