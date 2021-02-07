---
description: 詳細については、「アクティビティクラスを使用したワークフローアクティビティの作成」を参照してください。
title: アクティビティ クラスを使用したワークフロー アクティビティの作成
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: 0d3ffc88bacfd941dfa0c853991bf72045468323
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754941"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>アクティビティ クラスを使用したワークフロー アクティビティの作成

で Windows Workflow Foundation (WF) を使用してアクティビティを作成する最も基本的な方法 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] は、 <xref:System.Activities.Activity> 組み込みの [アクティビティライブラリ](net-framework-4-5-built-in-activity-library.md)からカスタムアクティビティまたはアクティビティをアセンブルして機能を作成するから継承するクラスを作成することです。 ここでは、2 つのメッセージをコンソールに書き込むアクティビティを作成する方法について説明します。

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>アクティビティ デザイナーを使ってカスタム アクティビティを作成するには

1. Visual Studio 2012 を開きます。

2. [ファイル]、[新規作成]、[プロジェクト] の順にクリックします。 [**プロジェクトの種類**] ウィンドウの [ **Visual C#** ] で [**ワークフロー 4.0** ] を選択し、[ **v2010** ] ノードを選択します。 [**テンプレート**] ウィンドウで [**アクティビティライブラリ**] を選択します。 新しいプロジェクトに HelloActivity という名前を付けます。

3. 新しいアクティビティを開きます。  <xref:System.Activities.Statements.Sequence> アクティビティをツールボックスからデザイナー画面にドラッグします。

4. <xref:System.Activities.Statements.WriteLine> アクティビティを <xref:System.Activities.Statements.Sequence> アクティビティにドラッグします。 `"Hello World"`**テキスト** フィールドに「」 (引用符を含む) と入力します。

5. 2 つ目の <xref:System.Activities.Statements.WriteLine> アクティビティを、1 つ目の下にある <xref:System.Activities.Statements.Sequence> アクティビティにドラッグします。 `"Goodbye"`**テキスト** フィールドに「」 (引用符を含む) と入力します。
