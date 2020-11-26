---
title: 108 - CustomTrackingRecordInfo
ms.date: 03/30/2017
ms.assetid: 5bee501e-4e00-42cd-b949-e88009c3d4e8
ms.openlocfilehash: 5fe45d62446d4dee23d29bed03dd490d8cb8efb8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238848"
---
# <a name="108---customtrackingrecordinfo"></a>108 - CustomTrackingRecordInfo

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|Id|108|  
|Keywords|UserEvents、EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Description  

 このイベントは、ワークフロー インスタンス内のアクティビティが情報レベルで CustomTrackingRecord を生成したときに、ETW 追跡参加要素によって生成されます。  
  
## <a name="message"></a>Message  

 TrackRecord = CustomTrackingRecord、InstanceID = %1、RecordNumber=%2、EventTime=%3、Name=%4、ActivityName=%5、ActivityId=%6、ActivityInstanceId=%7、ActivityTypeName=%8、Data=%9、Annotations=%10、ProfileName = %11  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ワークフローのインスタンス ID|  
|RecordNumber|xs:long|生成されたレコードのシーケンス番号|  
|EventTime|xs:dateTime|イベントの生成時刻 (UTC)|  
|名前|xs:string|CustomTrackingRecord の名前|  
|ActivityName|xs:string|CustomTrackingRecord を出力するアクティビティの名前|  
|ActivityId|xs:string|CustomTrackingRecord を出力するアクティビティの ID|  
|ActivityInstanceId|xs:string|CustomTrackingRecord を出力するアクティビティのインスタンス|  
|ActivityTypeName|xs:string|CustomTrackingRecord を出力するアクティビティの名前|  
|Data|xs:string|このイベントで追跡されたデータ。  値は、datavalue 形式の xml 要素に格納され \<items> \< item  name = "dataName" type="System.String"> \</item> \</items> ます。  データが追跡されていない場合は、文字列にが含まれ \<items/> ます。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えると、注釈が削除され、データ値が... に置き換えられて、イベントが切り捨てられます。 \<items> \</items> 次の型は、ToString () によって返される値として格納されます。string、char、bool、int、short、long、uint、ushort、ulong、system.string、float、double、System.guid、system.string、system.string、および system.string。  その他のすべての型は、System.Runtime.Serialization.NetDataContractSerializer を使用してシリアル化されます。|  
|注釈|xs:string|このイベントに追加された注釈。  値は、annotationValue 形式の xml 要素に格納され \<items> \< item  name = "annotationName" type="System.String"> \</item> \</items> ます。  注釈が指定されていない場合、文字列にはが含まれ \<items/> ます。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えると、注釈が削除され、注釈の値が... に置き換えられて、イベントが切り捨てられます。 \<items> \</items>|  
|ProfileName|xs:string|このイベントを生成した追跡プロファイルの名前|  
|HostReference|xs:string|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。  この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。例: ' Default Web Site/電卓 '&#124;&#124;|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
