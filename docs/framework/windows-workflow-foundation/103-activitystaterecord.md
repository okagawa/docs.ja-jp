---
title: 103 - ActivityStateRecord
ms.date: 03/30/2017
ms.assetid: 57636a9a-561e-44aa-aef9-1f1894aaa6dd
ms.openlocfilehash: 02c33f02b7650c9f9b7527c319de3b58980fdd6c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275077"
---
# <a name="103---activitystaterecord"></a>103 - ActivityStateRecord

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|Id|103|  
|Keywords|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Description  

 このイベントは、ワークフロー インスタンス内のアクティビティが ActivityStateRecord を生成したときに、ETW 追跡参加要素によって生成されます。  
  
## <a name="message"></a>Message  

 TrackRecord = ActivityStateRecord、InstanceID = %1、RecordNumber=%2、EventTime=%3、State = %4、Name=%5、ActivityId=%6、ActivityInstanceId=%7、ActivityTypeName=%8、Arguments=%9、Variables=%10、Annotations=%11、ProfileName = %12  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ワークフローのインスタンス ID|  
|RecordNumber|xs:long|生成されたレコードのシーケンス番号|  
|EventTime|xs:dateTime|イベントの生成時刻 (UTC)|  
|State|xs:string|アクティビティの状態|  
|名前|xs:string|イベントを生成したアクティビティの表示名|  
|ActivityId|xs:string|生成したアクティビティのアクティビティ ID|  
|ActivityInstanceId|xs:string|生成したアクティビティのアクティビティ インスタンス ID|  
|ActivityTypeName|xs:string|生成したアクティビティの型名|  
|引数|xs:string|このイベントで追跡された引数。  値は、argumentvalue の形式で xml 要素に格納され \<items> \< item  name = "argumentName" type="System.String"> \</item> \</items> ます。  引数が追跡されなかった場合、文字列にはが含まれ \<items/> ます。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えると、注釈が削除され、注釈の値が... に置き換えられて、イベントが切り捨てられます。 \<items> \</items> 次の型は、ToString () によって返される値として格納されます。string、char、bool、int、short、long、uint、ushort、ulong、system.string、float、double、System.guid、system.string、system.string、および system.string。  その他のすべての型は、System.Runtime.Serialization.NetDataContractSerializer を使用してシリアル化されます。|  
|変数|xs:string|このイベントで追跡された変数。  値は、形式の変数値の xml 要素に格納され \<items> \< item  name = "variableName" type="System.String"> \</item> \</items> ます。  変数が追跡されなかった場合、文字列にはが含まれ \<items/> ます。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えると、注釈が削除され、変数の値が... に置き換えられて、イベントが切り捨てられます。 \<items> \</items> 次の型は、ToString () によって返される値として格納されます。string、char、bool、int、short、long、uint、ushort、ulong、system.string、float、double、System.guid、system.string、system.string、および system.string。  その他のすべての型は、System.Runtime.Serialization.NetDataContractSerializer を使用してシリアル化されます。|  
|注釈|xs:string|このイベントに追加された注釈。  値は、annotationValue 形式の xml 要素に格納され \<items> \< item  name = "annotationName" type="System.String"> \</item> \</items> ます。  注釈が指定されていない場合、文字列にはが含まれ \<items/> ます。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えると、注釈が削除され、注釈の値が... に置き換えられて、イベントが切り捨てられます。 \<items> \</items>|  
|ProfileName|xs:string|このイベントを生成した追跡プロファイルの名前|  
|HostReference|xs:string|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。  この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。例: ' Default Web Site/電卓 '&#124;&#124;|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
