---
description: 詳細については、「ActivityTransfer」を参照してください。
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 28f7d1c0d1056327313e7aa6be293eb325d8f265
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99758009"
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
