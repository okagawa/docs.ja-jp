---
title: 1148 - FlowchartSwitchCaseNotFound
ms.date: 03/30/2017
ms.assetid: 9ee7fcee-e040-4306-968e-ed840a1cb00c
ms.openlocfilehash: fb9f4be3dba0f8632f1ae074ad9ddb726c5d84ab
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241708"
---
# <a name="1148---flowchartswitchcasenotfound"></a>1148 - FlowchartSwitchCaseNotFound

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1148|  
|Keywords|WFActivities|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Description  

 フローチャート スイッチの一致の例および既定の例のいずれも見つけることができなかったことを示します。 フローチャートの実行は終了します。  
  
## <a name="message"></a>Message  

 Flowchart '%1'/FlowSwitch - 式の結果に一致する Case アクティビティも Default Case も見つかりませんでした。 フローチャートの実行は終了します。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|FlowChart|xs:string|FlowChart の表示名。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
