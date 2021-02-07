---
description: '詳細については、次を参照してください: WSAT_TraceRecord'
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 67202c5d2910783c40b934d2da6108e6b514a728
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756878"
---
# <a name="wsat_tracerecord"></a>WSAT_TraceRecord

WSAT_TraceRecord  
  
## <a name="syntax"></a>構文  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a>メソッド  

 WSAT_TraceRecord クラスで定義されるメソッドはありません。  
  
## <a name="properties"></a>プロパティ  

 WSAT_TraceRecord クラスには、次のプロパティがあります。  
  
### <a name="activityid"></a>ActivityID  

 データ型: object  
アクセスの種類: 読み取り専用  
  
 トレース レコードのアクティビティ ID です。  
  
### <a name="eventid"></a>EventID  

 データ型 : sint32  
アクセスの種類: 読み取り専用  
  
 トレース レコードのイベント ID です。  
  
### <a name="tracerecord"></a>TraceRecord  

 データ型: 文字列  
アクセスの種類: 読み取り専用  
  
 トレース レコード  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|
