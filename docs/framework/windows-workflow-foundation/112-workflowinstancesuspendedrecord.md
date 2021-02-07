---
description: '詳細情報: 112-WorkflowInstanceSuspendedRecord'
title: 112 - WorkflowInstanceSuspendedRecord
ms.date: 03/30/2017
ms.assetid: bc825c7c-8c90-48f7-9336-9a978a8246c6
ms.openlocfilehash: 6d2088da6e395476bba05d5e2f4557ea527ecdd8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667396"
---
# <a name="112---workflowinstancesuspendedrecord"></a>112 - WorkflowInstanceSuspendedRecord

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|Id|112|  
|Keywords|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 このイベントは、ワークフロー インスタンスが WorkflowInstanceSuspended Record を生成したときに、ETW 追跡参加要素によって生成されます。  
  
## <a name="message"></a>Message  

 TrackRecord = WorkflowInstanceSuspendedRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、Reason = %5、Annotations = %6、ProfileName = %7  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ワークフローのインスタンス ID|  
|RecordNumber|xs:long|生成されたレコードのシーケンス番号|  
|EventTime|xs:dateTime|イベントの生成時刻 (UTC)|  
|ActivityDefinitionId|xs:string|ワークフローのルート アクティビティの名前|  
|理由|xs:string|ワークフローの中断の理由。|  
|注釈|xs:string|このイベントに追加された注釈。  値は、annotationValue 形式の xml 要素に格納され \<items> \< item  name = "annotationName" type="System.String"> \</item> \</items> ます。  注釈が指定されていない場合、文字列にはが含まれ \<items/> ます。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えると、注釈が削除され、注釈の値が... に置き換えられて、イベントが切り捨てられます。 \<items> \</items>|  
|ProfileName|xs:string|このイベントを生成した追跡プロファイルの名前|  
|HostReference|xs:string|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。  この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。例: ' Default Web Site/電卓 '&#124;&#124;|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
