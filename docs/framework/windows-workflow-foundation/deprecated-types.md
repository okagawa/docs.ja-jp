---
title: Windows Workflow Foundation で非推奨の型
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: 628963650d32237dedbb6ab2a0a2d9a79866af18
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272873"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Windows Workflow Foundation で非推奨の型

.NET 4 の段階で、ワークフロー チームは、<xref:System.Activities> 名前空間のまったく新しいワークフロー エンジンをリリースしました。 .NET Framework 4.5 Beta のリリースでは、"WF 3"、、および名前空間のほとんどの型を <xref:System.Workflow.Activities> <xref:System.Workflow.ComponentModel>  <xref:System.Workflow.Runtime> 廃止としてマークしています。

## <a name="obsolete-namespaces-and-tools"></a>旧式の名前空間とツール

 次のアセンブリには、今後非推奨とされるパブリック型が 1 つ以上含まれています：

- System.Workflow.Activities.dll

- System.Workflow.ComponentModel.dll

- System.Workflow.Runtime.dll

- System.WorkflowServices.dll

- Microsoft.Workflow.DebugController.dll

- Microsoft.Workflow.Compiler.exe

- Wfc.exe

 その結果、非推奨とされた WF 3 API を今後使用すると、ビルド時に警告が発生し、次のようなメッセージが表示されます：

 **警告 BC40000: X は互換性のために残されています: WF 3 の型は非推奨とされます。代わりに、WF 4 を使用してください。** WF 3 の型は .NET Framework の将来のリリースで削除されますが、実際の削除時期はまだ未定です (4.5 では行われません)。 この段階的な変更は、今後の方向性を示し、お客様が WF 4 モデルに余裕をもって移行するための期間を確保するためのものです。 もちろん、 [Microsoft サポートライフサイクルポリシー](/lifecycle/)では、これらの WF 3 の種類を引き続きサポートします。 既存の WF3 アプリケーションは .NET Framework 4.5 では問題なく実行され、Visual Studio 2012 は新規および既存の WF3 ベースのソリューションをサポートします。

 <xref:System.Workflow.Activities.Rules> 名前空間に含まれるルール関連の型については、WF 4.5 には相当する型がないため、非推奨扱いにはなりません。

 WF 4 にアプリケーションを移行するお客様は、 [ワークフロー4の移行](migration-guidance.md)に関するガイダンスのヘルプを参照してください。
