---
title: トランザクションの例外
ms.date: 03/30/2017
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
ms.openlocfilehash: dcdf825699368617335f2d59a05f8826884a8e9e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285682"
---
# <a name="transaction-exceptions"></a>トランザクションの例外

このトピックでは、Windows Communication Foundation (WCF) トランザクションによって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|メタデータからインポートされたポリシー情報により、TransactionProtocol に操作間で異なる値が指定されました。 各エンドポイントでサポートされる TransactionProtocol は 1 つに限られます。|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|TransactionAutoComplete は、サービスの InstanceContextMode が PerSession にならない限り、false にはなりません。 指定したコントラクトと操作の実装でエラーが発生しました。|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete は、TransactionAutoComplete が false に設定され、TransactionScopeRequired が true に設定されている場合にのみ、操作から呼び出すことができます。 これは無効なシナリオであり、現在のトランザクションは終了しました。|  
|TransactionFlowRequiredIssuedTokens|トランザクションをフローさせるには、発行済みトークンのフローもサポートされる必要があります。|  
|TrustDriverVersionDoesNotSupportIssuedTokens|構成されたバージョンの Trust では、発行済みトークンがサポートされません。 WSTrustFeb2005 またはそれ以降を使用してください。|
