---
description: '詳細情報: OperationBehaviorAttribute'
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: c1f1b80134163ee65d5015e52017f5bb455aeac7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803062"
---
# <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute

OperationBehaviorAttribute  
  
## <a name="syntax"></a>構文  
  
```csharp
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a>メソッド  

 OperationBehaviorAttribute クラスで定義されるメソッドはありません。  
  
## <a name="properties"></a>プロパティ  

 OperationBehaviorAttribute クラスには、次のプロパティがあります。  
  
### <a name="autodisposeparameters"></a>AutoDisposeParameters  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 パラメーターの自動破棄機能の状態です。  
  
### <a name="impersonation"></a>偽装  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 操作がサポートする、呼び出し元の偽装レベルを示します。  
  
### <a name="releaseinstancemode"></a>ReleaseInstanceMode  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 操作の呼び出し過程のどの時点でオブジェクトをリサイクルするかを示します。  
  
### <a name="transactionautocomplete"></a>TransactionAutoComplete  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 未処理の例外が発生しなかった場合に、現在のトランザクションを自動的にコミットするかどうかを示します。  
  
### <a name="transactionscoperequired"></a>TransactionScopeRequired  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 操作がトランザクションを必要とするかどうかを示します。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.OperationBehaviorAttribute>
