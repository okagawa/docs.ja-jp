---
description: 詳細については <services> 、 <workflowRuntime>
title: <services> の <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 219a05b1-f573-45c9-849b-e86bc373b62f
ms.openlocfilehash: 87cac8903263b4588db43c15d7849dcd7443d41c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682801"
---
# <a name="services-of-workflowruntime"></a>\<services> の \<workflowRuntime>

<xref:System.Workflow.Runtime.WorkflowRuntime> エンジンに追加されるサービスのコレクションを表します。 要素は、<xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> 型です。  コレクションで指定されたサービスはワークフロー ランタイム エンジンによって初期化され、適切な <xref:System.Workflow.Runtime.WorkflowRuntime> コンストラクターが呼び出されるとワークフロー ランタイム エンジンのサービスに追加されます。 したがって、コレクションで指定されたサービスは、そのコンストラクターのシグネチャに関して一定の規則に従う必要があります。 詳細については、「<xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- [ワークフロー構成ファイル](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
