---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 05278067e3f86612ee4aafbe7d5eb66dc934cb85
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242111"
---
# <a name="3502---inferredoperationdescription"></a>3502 - InferredOperationDescription

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|3502|  
|Keywords|WFServices|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Description  

 OperationDescription が WorkflowService から推論されたことを示します。  
  
## <a name="message"></a>Message  

 コントラクト '%2' 内の Name='%1' の OperationDescription が WorkflowService から推論されました。 IsOneWay=%3。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:string|操作の名前。|  
|ContractName|xs:string|コントラクトの名前。|  
|IsOneWay|xs:string|True または False はコントラクトが一方向かどうかを示します。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
