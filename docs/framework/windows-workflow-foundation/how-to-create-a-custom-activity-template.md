---
description: '詳細については、「方法: カスタムアクティビティテンプレートを作成する」を参照してください。'
title: '方法: カスタム アクティビティ テンプレートを作成する'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: 06fda953110e36e46a91fda8697aadbcd6e6bf59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742109"
---
# <a name="how-to-create-a-custom-activity-template"></a>方法: カスタム アクティビティ テンプレートを作成する

カスタム複合アクティビティなどのアクティビティの構成のカスタマイズには、カスタム アクティビティ テンプレートが使用されるため、手動で各アクティビティを個別に作成し、そのプロパティおよびその他の設定を構成する必要はありません。 これらのカスタムテンプレートは、Windows ワークフローデザイナーの **ツールボックス** 、または再ホストされたデザイナーから使用できます。ユーザーは、これらのテンプレートを使用して、構成済みのデザインサーフェイスにドラッグできます。 ワークフローデザイナーには、[[メッセージングアクティビティデザイナー](/visualstudio/workflow-designer/messaging-activity-designers) ] カテゴリの[sendandreceivereply テンプレートデザイナー](/visualstudio/workflow-designer/sendandreceivereply-template-designer)と[receiveandsendreply テンプレートデザイナー](/visualstudio/workflow-designer/receiveandsendreply-template-designer)の適切なテンプレートの例が付属しています。

 このトピックの最初の手順では、 **Delay** アクティビティ用のカスタムアクティビティテンプレートを作成する方法について説明します。2番目の手順では、カスタムテンプレートが動作するかどうかを確認するためにワークフローデザイナーで使用できるようにする方法について簡単に説明します。

 カスタム アクティビティ テンプレートに <xref:System.Activities.Presentation.IActivityTemplateFactory> を実装する必要があります。 このインターフェイスには単一の <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> メソッドがあり、このメソッドを使用して、テンプレートで使用されるアクティビティ インスタンスを作成および構成できます。

## <a name="to-create-a-template-for-the-delay-activity"></a>Delay アクティビティのテンプレートを作成するには

1. Visual Studio 2010 を起動します。

2. **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3. [**プロジェクトの種類**] ペインで、使用している言語に応じて、 **Visual C#** プロジェクトまたは **Visual Basic** グループから [**ワークフロー** ] を選択します。

4. [ **テンプレート** ] ウィンドウで、[ **アクティビティライブラリ**] を選択します。

5. **[名前]** ボックスに、「`DelayActivityTemplate`」と入力します。

6. [ **場所** ] と [ **ソリューション名** ] のテキストボックスの既定値をそのまま使用し、[ **OK]** をクリックします。

7. **ソリューションエクスプローラー** で DelayActivityTemplate プロジェクトの References ディレクトリを右クリックし、[**参照の追加**] をクリックして [参照の **追加**] ダイアログボックスを開きます。

8. [ **.Net** ] タブに移動し、左側の [**コンポーネント名**] 列で [**プレゼンテーションフレームワーク**] を選択し、[ **OK** ] をクリックして PresentationFramework.dll ファイルへの参照を追加します。

9. この手順を繰り返して、System.Activities.Presentation.dll ファイルと WindowsBase.dll ファイルへの参照を追加します。

10. **ソリューションエクスプローラー** で DelayActivityTemplate プロジェクトを右クリックし、[**追加**]、[**新しい項目**] の順に選択して [**新しい項目の追加**] ダイアログボックスを開きます。

11. **クラス** テンプレートを選択し、MyDelayTemplate という名前を指定して、[ **OK]** をクリックします。

12. MyDelayTemplate.cs ファイルを開き、次のステートメントを追加します。

    ```csharp
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. 次のコードを使用して、<xref:System.Activities.Presentation.IActivityTemplateFactory> クラスを持つ `MyDelayActivity` を実装します。 これにより、10 秒間の遅延が構成されます。

    ```csharp
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
    ```

14. [**ビルド**] メニューの [**ソリューションのビルド**] を選択して、DelayActivityTemplate.dll ファイルを生成します。

### <a name="to-make-the-template-available-in-a-workflow-designer"></a>ワークフロー デザイナーでテンプレートを利用できるようにするには

1. **ソリューションエクスプローラー** で DelayActivityTemplate ソリューションを右クリックし、[**追加**]、[**新しいプロジェクト**] の順に選択して [**新しいプロジェクトの追加**] ダイアログボックスを開きます。

2. [ **ワークフローコンソールアプリケーション** ] テンプレートを選択し、という名前を指定して `CustomActivityTemplateApp` 、[ **OK]** をクリックします。

3. **ソリューションエクスプローラー** で CustomActivityTemplateApp プロジェクトの References ディレクトリを右クリックし、[**参照の追加**] をクリックして [参照の **追加**] ダイアログボックスを開きます。

4. [**プロジェクト**] タブに移動し、左側の [**プロジェクト名**] 列から [ **delayactivitytemplate** ] を選択し、[ **OK** ] をクリックして、最初の手順で作成した DelayActivityTemplate.dll ファイルへの参照を追加します。

5. **ソリューションエクスプローラー** で CustomActivityTemplateApp プロジェクトを右クリックし、[**ビルド**] を選択してアプリケーションをコンパイルします。

6. **ソリューションエクスプローラー** で CustomActivityTemplateApp プロジェクトを右クリックし、[**スタートアッププロジェクトに設定**] を選択します。

7. [**デバッグ**] メニューの [**デバッグなしで開始**] を選択し、任意のキーを押して cmd.exe ウィンドウでメッセージが表示されたら操作を続行します。

8. Workflow1.xaml ファイルを開き、 **ツールボックス** を開きます。

9. **Delayactivitytemplate** カテゴリで **mydelayactivity** テンプレートを見つけます。 デザイン サーフェイスにドラッグします。 [ **プロパティ** ] ウィンドウで、 `Duration` プロパティが10秒に設定されていることを確認します。

## <a name="example"></a>例

 MyDelayActivity.cs ファイルには次のコードが含まれます。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

//Namespaces added
using System.Activities;
using System.Activities.Statements;
using System.Activities.Presentation;
using System.Windows;

namespace DelayActivityTemplate
{
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
}
```

## <a name="see-also"></a>関連項目

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [ワークフロー デザイン操作のカスタマイズ](customizing-the-workflow-design-experience.md)
