---
title: WF のステート マシン アクティビティ
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: dd0bfae1f24ecd9f98c0a2f04265581f880202a7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261723"
---
# <a name="state-machine-activities-in-wf"></a>WF のステート マシン アクティビティ

.NET Framework 4.5 には、システムによって提供されるアクティビティと、ステートマシンワークフローを作成するためのアクティビティデザイナーが用意されています。  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|使い慣れたステート マシン パラダイムを使用して、含まれているアクティビティを実行します。|  
|<xref:System.Activities.Statements.State>|ステート マシンの状態を表します。|  
|<xref:System.Activities.Core.Presentation.FinalState>|ステート マシンの最終状態を表します。 <xref:System.Activities.Core.Presentation.FinalState> は、使用すると、最終状態として事前に構成済みの <xref:System.Activities.Statements.State> を作成するアクティビティ デザイナーです。 詳細については、「 [Finalstate アクティビティデザイナー](/visualstudio/workflow-designer/finalstate-activity-designer)」を参照してください。|  
|<xref:System.Activities.Statements.Transition>|2 つの状態間の遷移を表します。 用の **ツールボックス** アイテムはありません <xref:System.Activities.Statements.Transition> 。遷移は、ワークフローデザイナーで2つの状態の間の線をドラッグアンドドロップするか、ある状態を別の状態に移動したときに表示される三角形の状態を削除することによって作成されます。 詳細については、「 [Transition アクティビティデザイナー](/visualstudio/workflow-designer/transition-activity-designer)」を参照してください。|  
  
## <a name="see-also"></a>関連項目

- [チュートリアル入門](getting-started-tutorial.md)
