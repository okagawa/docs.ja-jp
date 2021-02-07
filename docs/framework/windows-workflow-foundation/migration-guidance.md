---
description: '詳細情報: 移行ガイダンス'
title: 移行のガイドライン
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 05aede02d7ad615ddeeceab6d71a545db9bcf5ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755355"
---
# <a name="migration-guidance"></a>移行のガイドライン

.NET Framework 4 では、Microsoft は、Windows Workflow Foundation (WF) の2番目のメジャーバージョンをリリースしています。 [!INCLUDE[wf1](../../../includes/wf1-md.md)] は WinFX でリリースされました (これには WF3 の型が含まれるようになり、現在はと呼ばれるようになりました \* )。また .NET Framework 3.5 でも強化されました。 WF3 も .NET Framework 4 に含まれていますが、新しいワークフローテクノロジ (WF4 と呼ばれる型) と共に存在し \* ます。 WF4 の導入時期を検討する場合は、最初にそのタイミングの管理を認識することが重要です。

- WF3 は .NET Framework 4 の完全にサポートされている部分です。

- WF3 アプリケーションは、変更せずに .NET Framework 4 で実行され、引き続き完全にサポートされます。

- 新しい WF3 アプリケーションを作成し、既存のアプリケーションを Visual Studio 2012 で編集し、完全にサポートすることができます。

 したがって、.NET Framework 4 を採用するかどうかの決定は、 \* WF3 (WF4) から () に移動するかどうかを決定するものとは分離されています。 \* このトピックでは、WF の移行のガイドラインへのリンクを提供し、WF3 および WF4 での作業に関する情報を提供します。

## <a name="wf-migration-white-papers-and-cookbooks"></a>WF の移行に関するホワイトペーパーと料理

 [WF の移行の概要](/previous-versions/appfabric/ff383417(v=azure.10))に関するトピックでは、WF3 と WF4 の間の関係と移行戦略の概要について説明します。 関連トピックでは、特定のトピックを掘り下げて説明します。

 [WF の移行の概要](/previous-versions/appfabric/ff383417(v=azure.10)) WF3 と WF4 の関係、および .NET Framework 4 のワークフローテクノロジのユーザーまたは潜在的なユーザーとしての選択肢について説明します。

 [WF の移行: WF3 開発のベストプラクティス](/previous-versions/appfabric/ff383417(v=azure.10)) WF4 に簡単に移行できるように WF3 アーティファクトを設計する方法について説明します。

 [WF のガイダンス: ルール](/previous-versions/appfabric/ff383417(v=azure.10)) .NET Framework 4 つのソリューションにルール関連の投資を進める方法について説明します。

 [WF のガイダンス: ステートマシン](/previous-versions/appfabric/ff383417(v=azure.10)) State-Machine アクティビティが存在しない場合の WF4 制御フローのモデリングについて説明します。

 このガイダンスは、.NET Framework 4 を対象とするワークフロー プロジェクトにのみ該当することに注意してください。 ステートマシンのワークフローは、Platform Update 1 のリリースで .NET Framework 4.0.1 に追加され、.NET Framework 4.5 の一部として含まれていました。 .NET Framework 4.0.1-4.0.3 と .NET Framework 4.5 のステートマシンワークフローの詳細については、「 [Update 4.0.1 for Microsoft .NET Framework 4 Features](/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) And [state machine ワークフロー](state-machine-workflows.md)」を参照してください。

 [WF の移行のクックブック: カスタムアクティビティ](/previous-versions/appfabric/ff383417(v=azure.10)) WF4 で WF3 カスタムアクティビティを再設計するための例と手順について説明します。

 [WF の移行のクックブック: 高度なカスタムアクティビティ](/previous-versions/appfabric/ff383417(v=azure.10)) WF3 キューを使用する advanced WF3 カスタムアクティビティを再設計し、子アクティビティを WF4 カスタムアクティビティとしてスケジュール設定するためのガイダンスを提供します。

 [WF の移行のクックブック: ワークフロー](/previous-versions/appfabric/ff383417(v=azure.10)) WF4 で WF3 ワークフローを再設計するための例と手順について説明します。

 [WF の移行のクックブック: ワークフローホスティング](/previous-versions/appfabric/ff383417(v=azure.10)) WF3 ホスティングコードを WF4 ホスティングコードとして再設計するためのガイダンスを提供します。 この目的は、WF3 と WF4 のワークフロー ホスティングの主な違いを説明することです。

 [WF の移行のクックブック: ワークフロー追跡](/previous-versions/appfabric/ff383417(v=azure.10)) 同等の WF4 追跡コードと構成を使用して、WF3 追跡コードと構成を再設計するためのガイダンスを提供します。

 [WF のガイダンス: ワークフローサービス](/previous-versions/appfabric/ff383417(v=azure.10)) 既定のアクティビティの一般的なシナリオで WF4 を使用するために、WF3 で作成された Windows Communication Foundation (WCF) web サービス (一般的にはワークフローサービスと呼ばれます) を実装するワークフローを再設計する例を示します。

## <a name="see-also"></a>関連項目

- <xref:System.Activities.Statements.Interop>
