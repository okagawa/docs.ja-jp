---
description: '詳細情報: 115-WorkflowInstanceAbortedRecordWithId'
title: 115 - WorkflowInstanceAbortedRecordWithId
ms.date: 03/30/2017
ms.assetid: 0293dd4e-e6ae-473a-b3d6-c2d38f9bd875
ms.openlocfilehash: 6d9eb387ba61a646cbf1423d01175b0230272ca5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755435"
---
# <a name="115---workflowinstanceabortedrecordwithid"></a>115 - WorkflowInstanceAbortedRecordWithId

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|id|115|  
|Keywords|HealthMonitoring、WFTracking|  
|Level|警告|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 このイベントは、ワークフロー インスタンスが WorkflowInstanceAbortedRecord を生成したときに、ETW 追跡参加要素によって生成されます。  
  
## <a name="message"></a>Message  

 TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、Reason = %5、Annotations = %6、ProfileName = %7、WorkflowDefinitionIdentity = %8  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ワークフローのインスタンス ID|  
|RecordNumber|xs:long|生成されたレコードのシーケンス番号|  
|EventTime|xs:dateTime|イベントの生成時刻 (UTC)|  
|ActivityDefinitionId|xs:string|ワークフローのルート アクティビティの名前|  
|State|xs:string|ワークフローの現在の状態。|  
|注釈|xs:string|このイベントに追加された注釈。 値は、annotationValue 形式の xml 要素に格納され \<items> \< item name = "annotationName" type="System.String"> \</item> \</items> ます。 注釈が指定されていない場合、文字列にはが含まれ \<items/> ます。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えると、注釈が削除され、注釈の値が... に置き換えられて、イベントが切り捨てられます。 \<items> \</items>|  
|ProfileName|xs:string|このイベントを生成した追跡プロファイルの名前|  
|WorkflowDefinitionIdentity|xs:string|ワークフロー定義 ID|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
