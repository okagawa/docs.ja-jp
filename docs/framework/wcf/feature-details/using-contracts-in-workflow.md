---
description: 詳細については、「ワークフローでのコントラクトの使用」を参照してください。
title: ワークフロー内でのコントラクトの使用
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: d1ef5a4c494643d521a5fe045ff87c0cbeb34db1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632218"
---
# <a name="using-contracts-in-workflow"></a>ワークフロー内でのコントラクトの使用

サービスを実装するときは、サービスおよびサービスが送受信するデータを説明する一連のコントラクトを定義します。 データは、データコントラクトとメッセージコントラクトとして表されます。WCF サービスとワークフローサービスはどちらも、サービスの説明の一部としてデータコントラクトとメッセージコントラクトの定義を使用します。 サービス自体は、(WSDL の形で) メタデータを公開して、サービスの操作を説明します。 WCF では、サービス コントラクトと操作コントラクトによって、サービス、およびサービスがサポートする操作を定義します。 ただし、ワークフロー サービスでは、これらのコントラクトはビジネス プロセス自体の一部になり、コントラクト推論と呼ばれるプロセスによってメタデータとして公開されます。  
  
## <a name="contract-inference"></a>コントラクト推論  

 ワークフロー サービスが <xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされている場合は、ワークフローで見つかった一連のメッセージ アクティビティに基づいて、ワークフロー定義が確認され、コントラクトが生成されます。 具体的には、次のアクティビティとプロパティが、コントラクトの生成に使用されます。  
  
 <xref:System.ServiceModel.Activities.Receive> の利用状況  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <xref:System.ServiceModel.Activities.SendReply> の利用状況  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> の利用状況  
  
 コントラクト推論の結果は、WCF サービスと操作コントラクトと同じデータ構造を使用するサービスの説明になります。 この情報を使用して、ワークフロー サービス用に WSDL が公開されます。  
  
## <a name="see-also"></a>関連項目

- [ワークフロー サービス](workflow-services.md)
- [メッセージング アクティビティ](messaging-activities.md)
- [方法: メッセージング アクティビティを使用してワークフロー サービスを作成する](how-to-create-a-workflow-service-with-messaging-activities.md)
- [方法: 既存のサービス コントラクトを使用するワークフロー サービスを作成する](../../windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
