---
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: 867219130fc853f3ba2c1c2f807b1651f6480f13
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273972"
---
# <a name="servicetimeoutsbehavior"></a>ServiceTimeoutsBehavior

ServiceTimeoutsBehavior  
  
## <a name="syntax"></a>構文  
  
```csharp
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a>メソッド  

 ServiceTimeoutsBehavior クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 ServiceTimeoutsBehavior クラスには、次のプロパティがあります。  
  
### <a name="transactiontimeout"></a>TransactionTimeout  

 データ型 : datetime  
  
 アクセスの種類: 読み取り専用  
  
 トランザクションを完了しなければならない期間。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
