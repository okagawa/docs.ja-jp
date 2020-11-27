---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: f1978881517fe5010ccc0f5192b21bd6688f063a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291116"
---
# <a name="activitytransfer"></a>ActivityTransfer

アクティビティ転送イベント  
  
## <a name="syntax"></a>構文  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a>メソッド  

 ActivityTransfer クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 ActivityTransfer クラスには次のプロパティがあります。  
  
### <a name="activityid"></a>ActivityID  
  
- データ型: object  
    アクセスの種類: 読み取り専用  
  
- アクティビティ ID  
  
### <a name="relatedactivityid"></a>RelatedActivityID  
  
- データ型: object  
    アクセスの種類: 読み取り専用  
  
- 関連アクティビティ ID  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|
