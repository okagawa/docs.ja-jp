---
title: COM+ と ServiceModel でのトランザクションの比較
ms.date: 03/30/2017
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
ms.openlocfilehash: 30ecbd374e909141dbc944740f90c1b41ac44ed2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264909"
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>COM+ と ServiceModel でのトランザクションの比較

このトピックでは、名前空間に用意されている Windows Communication Foundation (WCF) 属性を使用して、トランザクション COM + サービスの動作をシミュレートする方法について説明 <xref:System.ServiceModel> します。  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>ServiceModel 属性を使った COM+ のエミュレート  

 次の表は、 <xref:System.EnterpriseServices.TransactionOption> トランザクションの作成に使用される列挙と、その `EnterpriseServices` トランザクションが名前空間で提供される WCF 属性とどのように関連付けられているかを比較したもの <xref:System.ServiceModel> です。  
  
|COM+ 属性|WCF 属性|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute> が <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> に設定されます。<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> が `true`です。<br /><br /> バインド要素の `TransactionFlow` 属性は `false` です。|  
|必須|<xref:System.ServiceModel.TransactionFlowAttribute> が <xref:System.ServiceModel.TransactionFlowOption.Allowed> に設定されます。<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> が `true`です。<br /><br /> バインド要素の `TransactionFlow` 属性は `true` です。|  
|サポートされています|同等の属性はありません。 一般に、`Required` を指定した場合の動作を採用することをお勧めします。|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> は `false` です。<br /><br /> バインド要素の `TransactionFlow` 属性は `false` です。|  
|無効|同等の属性はありません。 一般に、`NotSupported` を指定した場合の動作を採用することをお勧めします。|
