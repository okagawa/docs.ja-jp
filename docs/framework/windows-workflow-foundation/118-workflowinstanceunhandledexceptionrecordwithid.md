---
title: 118 - WorkflowInstanceUnhandledExceptionRecordWithId
ms.date: 03/30/2017
ms.assetid: 2ce4b193-e141-4cc4-86a3-2e8c984c110d
ms.openlocfilehash: 54bbb267902fe547821d4a5580f86da944ae70cd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278688"
---
# <a name="118---workflowinstanceunhandledexceptionrecordwithid"></a>118 - WorkflowInstanceUnhandledExceptionRecordWithId

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|118|  
|Keywords|HealthMonitoring、WFTracking|  
|Level|エラー|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Description  

 このイベントは、ワークフロー インスタンスが WorkflowInstanceUnhandledExceptionRecord を生成したときに、ETW 追跡参加要素によって生成されます。  
  
## <a name="message"></a>Message  

 TrackRecord = WorkflowInstanceUnhandledExceptionRecord, InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、SourceName = %5、SourceId = %6、SourceInstanceId = %7、SourceTypeName=%8、Exception=%9、Annotations= %10、ProfileName = %11、WorkflowDefinitionIdentity = %12  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ワークフローのインスタンス ID|  
|RecordNumber|xs:long|生成されたレコードのシーケンス番号|  
|EventTime|xs:dateTime|イベントの生成時刻 (UTC)|  
|ActivityDefinitionId|xs:string|ワークフローのルート アクティビティの名前|  
|SourceName|xs:string|失敗して unhandledException が発生した原因のアクティビティ名|  
|SourceId|xs:string|エラーの原因であるアクティビティのアクティビティ ID|  
|SourceInstanceId|xs:string|エラーの原因であるアクティビティのアクティビティ インスタンス ID|  
|SourceTypeName|xs:string|失敗して unhandledException が発生した原因のアクティビティの型名|  
|例外|xs:string|ハンドルされない例外の詳細|  
|State|xs:string|ワークフローの現在の状態。|  
|注釈|xs:string|このイベントに追加された注釈。 値は、annotationValue 形式の xml 要素に格納され \<items> \< item name = "annotationName" type="System.String"> \</item> \</items> ます。 注釈が指定されていない場合、文字列にはが含まれ \<items/> ます。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えると、注釈が削除され、注釈の値が... に置き換えられて、イベントが切り捨てられます。 \<items> \</items>|  
|ProfileName|xs:string|このイベントを生成した追跡プロファイルの名前|  
|WorkflowDefinitionIdentity|xs:string|ワークフロー定義 ID|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
