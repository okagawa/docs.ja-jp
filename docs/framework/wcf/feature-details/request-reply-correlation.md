---
description: 詳細については、「Request-Reply 関連付け」を参照してください。
title: 要求/応答の相関関係
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: e745c9061f227e08400973f43613da73e68c8d70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632842"
---
# <a name="request-reply-correlation"></a>要求/応答の相関関係

要求/応答の相関関係は、 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> ワークフローサービスに双方向の操作を実装するためにペアと共に使用され、 <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> 別の Web サービスで双方向の操作を実行するペアと共に使用されます。 WCF サービスで双方向の操作を呼び出す場合、サービスは、従来の命令型コードベースの Windows Communication Foundation (WCF) サービスにすることも、ワークフローサービスにすることもできます。 要求/応答の相関関係を使用するには、<xref:System.ServiceModel.BasicHttpBinding> などの双方向のバインドを使用する必要があります。 双方向の操作を呼び出す場合と実装する場合では、相関関係の初期化に同様の手順が使用されます。これらの手順については、このセクションで説明します。  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>Receive/SendReply による双方向の操作での相関関係の使用  

 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> ペアは、ワークフローサービスに双方向の操作を実装するために使用されます。 ランタイムは、要求/応答の相関関係を使用して、応答が正しい呼び出し元にディスパッチされるようにします。 ワークフローが <xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされている場合、つまり、ワークフロー サービスの場合は、既定の相関関係の初期化で十分です。 このシナリオでは、1つの <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> ペアがワークフローによって使用され、特定の相関関係の構成は必要ありません。  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
### <a name="explicitly-initializing-request-reply-correlation"></a>要求/応答の相関関係の明示的な初期化  

 他の双方向の操作が並列実行される場合、相関関係を明示的に構成する必要があります。 これを行うには、とを指定する <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> か、を内に配置し <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.CorrelationScope> ます。 この例では、要求/応答の相関関係がペアで構成されてい <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> ます。  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 相関関係を明示的に構成する代わりに、<xref:System.ServiceModel.Activities.CorrelationScope> アクティビティを使用することもできます。 <xref:System.ServiceModel.Activities.CorrelationScope> は、内包しているメッセージング アクティビティに暗黙の <xref:System.ServiceModel.Activities.CorrelationHandle> を提供します。 この例では、 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> ペアは内に含まれてい <xref:System.ServiceModel.Activities.CorrelationScope> ます。 明示的な相関関係の構成は不要です。  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
CorrelationScope s = new CorrelationScope  
{  
    Body = new Sequence  
    {  
        Activities =
        {  
            StartOrder,  
            // Activities that create the reply.  
            ReplyToStartOrder  
        }  
    }  
};  
  
// Construct a workflow using the CorrelationScope.  
```  
  
 追加の相関関係が必要な場合は、目的の種類の <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> を使用する各メッセージング アクティビティの `CorrelationInitializer` プロパティを使用して、追加の相関関係を構成します。  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>Send/ReceiveReply による双方向の操作での相関関係の使用  

 アクティビティは、 <xref:System.ServiceModel.Activities.Receive> によってホストされるワークフローサービスでのみ使用できますが、この <xref:System.ServiceModel.Activities.WorkflowServiceHost> <xref:System.ServiceModel.Activities.Send> ペアは、 <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> Web サービスでメソッドを呼び出す必要がある任意のワークフローで使用できます。 ワークフローが <xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされる場合は、前のセクションで説明した既定の相関関係が適用されますが、そうでない場合は、目的の <xref:System.ServiceModel.Activities.CorrelationInitializer> と <xref:System.ServiceModel.Activities.CorrelationHandle> を明示的に使用するか、<xref:System.ServiceModel.Activities.CorrelationScope> による暗黙の処理管理を使用して、相関関係を構成する必要があります。  
  
 双方向の操作を使用するサービスで **サービス参照の追加** を使用する場合、 <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> 明示的に指定された要求/応答の相関関係を使用してペアアクティビティを内部的にラップするアクティビティが生成されます。
