---
description: 詳細については、CodeActivity クラスを使用したワークフローアクティビティの作成に関するページを参照してください。
title: CodeActivity クラスを使用したワークフロー アクティビティの作成
ms.date: 03/30/2017
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
ms.openlocfilehash: 393b6c586a88e876484f6888441d5bb82b4c0dad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754915"
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a>CodeActivity クラスを使用したワークフロー アクティビティの作成

<xref:System.Activities.CodeActivity> を継承して作成されたアクティビティは、<xref:System.Activities.CodeActivity.Execute%2A> メソッドをオーバーライドすることで強制的な基本動作を実装できます。

## <a name="using-codeactivitycontext"></a>CodeActivityContext の使用

 ワークフロー ランタイムの機能は、<xref:System.Activities.CodeActivity.Execute%2A> 型の `context` パラメーターを使用して、<xref:System.Activities.CodeActivityContext> メソッド内からアクセスできます。 <xref:System.Activities.CodeActivityContext> を介して、以下のような機能を使用できます。

- 変数と引数の値を取得および設定。

- <xref:System.Activities.CodeActivityContext.Track%2A> を使用したカスタムの追跡機能。

- <xref:System.Activities.CodeActivityContext.GetProperty%2A> を使用したアクティビティの実行プロパティへのアクセス。

#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a>CodeActivity を継承するカスタム アクティビティを作成するには

1. Visual Studio 2010 を開きます。

2. [ **ファイル**]、[ **新規作成**]、[ **プロジェクト**] の順に選択します。 [**プロジェクトの種類**] ウィンドウの [ **Visual C#** ] で [**ワークフロー 4.0** ] を選択し、[ **v2010** ] ノードを選択します。 [**テンプレート**] ウィンドウで [**アクティビティライブラリ**] を選択します。 新しいプロジェクトに HelloActivity という名前を付けます。

3. HelloActivity プロジェクトで Activity1 を右クリックし、[ **削除**] を選択します。

4. HelloActivity プロジェクトを右クリックし、[ **追加** ]、[ **クラス**] の順に選択します。 新しいクラスに HelloActivity.cs という名前を付けます。

5. HelloActivity.cs ファイルで、次の `using` ディレクティブを追加します。

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. クラス宣言に基本クラスを追加することにより、新しいクラスで <xref:System.Activities.CodeActivity> から継承します。

    ```csharp
    class HelloActivity : CodeActivity
    ```

7. <xref:System.Activities.CodeActivity.Execute%2A> メソッドを追加して、このクラスに機能を追加します。

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <xref:System.Activities.CodeActivityContext> を使用して追跡レコードを作成します。

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));
        context.Track(record);
    }
    ```
