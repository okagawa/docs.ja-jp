---
description: '詳細情報: 3501-InferredContractDescription'
title: 3501 - InferredContractDescription
ms.date: 03/30/2017
ms.assetid: 21a70849-4fc0-41d2-b9a4-db5aa2acdf1a
ms.openlocfilehash: 2eab180780a1475bff421441b7cef23f58f627c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778088"
---
# <a name="3501---inferredcontractdescription"></a>3501 - InferredContractDescription

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|3501|  
|Keywords|WFServices|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 ContractDescription が WorkflowService から推論されたことを示します。  
  
## <a name="message"></a>Message  

 Name='%1' で Namespace='%2' の ContractDescription が WorkflowService から推論されました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|名前|xs:string|ContractDescription の名前。|  
|名前空間|xs:string|ContractDescription の名前空間。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
