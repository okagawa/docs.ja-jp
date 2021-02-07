---
description: '詳細情報: 104-ActivityScheduledRecord'
title: 104 - ActivityScheduledRecord
ms.date: 03/30/2017
ms.assetid: ae202178-8fb1-4646-a3aa-18beeda8ff93
ms.openlocfilehash: 9d52dac3ec68de0d38959e81294c5c6ead21428e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667812"
---
# <a name="104---activityscheduledrecord"></a>104 - ActivityScheduledRecord

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|Id|104|  
|Keywords|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|Level|Information|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  

 このイベントは、ワークフロー インスタンス内のアクティビティが ActivityScheduledRecord を生成したときに、ETW 追跡参加要素によって生成されます。  
  
## <a name="message"></a>Message  

 TrackRecord = ActivityScheduledRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、Name = %4、ActivityId = %5、ActivityInstanceId = %6、ActivityTypeName = %7、ChildActivityName = %8、ChildActivityId = %9、ChildActivityInstanceId = %10、ChildActivityTypeName =%11、Annotations=%12、ProfileName = %13  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ワークフローのインスタンス ID|  
|RecordNumber|xs:long|生成されたレコードのシーケンス番号|  
|EventTime|xs:dateTime|イベントの生成時刻 (UTC)|  
|名前|xs:string|子アクティビティをスケジュールしたアクティビティの名前|  
|ActivityId|xs:string|子アクティビティをスケジュールしたアクティビティの ID|  
|ActivityInstanceId|xs:string|子アクティビティをスケジュールしたアクティビティのインスタンス ID|  
|ActivityTypeName|xs:string|操作のキャンセルを要求したアクティビティの型|  
|ChildActivityName|xs:string|スケジュール済みアクティビティの名前|  
|ChildActivityId|xs:string|スケジュール済みアクティビティの ID|  
|ChildActivityInstanceId|xs:string|スケジュール済みアクティビティのインスタンス ID|  
|ChildActivityTypeName|xs:string|スケジュール済みアクティビティの型|  
|注釈|xs:string|このイベントに追加された注釈。  値は、annotationValue 形式の xml 要素に格納され \<items> \< item  name = "annotationName" type="System.String"> \</item> \</items> ます。  注釈が指定されていない場合、文字列にはが含まれ \<items/> ます。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えると、注釈が削除され、注釈の値が... に置き換えられて、イベントが切り捨てられます。 \<items> \</items>|  
|ProfileName|xs:string|このイベントを生成した追跡プロファイルの名前|  
|HostReference|xs:string|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。  この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。例: ' Default Web Site/電卓 '&#124;&#124;|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
