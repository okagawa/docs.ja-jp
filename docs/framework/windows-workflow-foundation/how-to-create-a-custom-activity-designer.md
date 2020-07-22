---
title: '方法: カスタム アクティビティ デザイナーを作成する'
description: この記事では、任意のアクティビティを配置できるドロップゾーンを持つ Workflow Foundation カスタムアクティビティデザイナーを作成する方法について説明します。
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: 015efd1e482e2b531d28b9caec411c76116c9653
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419786"
---
# <a name="how-to-create-a-custom-activity-designer"></a>方法: カスタム アクティビティ デザイナーを作成する

カスタム アクティビティ デザイナーは、通常、関連付けられたアクティビティを他のアクティビティと組み合わせることができるように実装されます。他のアクティビティのデザイナーは、アクティビティと一緒にデザイン サーフェイスにドロップできます。 この機能を使用するには、カスタムアクティビティデザイナーが、任意のアクティビティを配置できる "ドロップゾーン" を提供する必要があります。また、デザインサーフェイスで結果として生成される要素のコレクションを管理する手段も必要です。 ここでは、そのようなドロップ ゾーンを含むカスタム アクティビティ デザイナーを作成する方法と、デザイナー要素のコレクションを管理するために必要な編集機能を提供するカスタム アクティビティ デザイナーを作成する方法を説明します。

カスタム アクティビティ デザイナーは、通常、<xref:System.Activities.Presentation.ActivityDesigner> を継承します。これは、特定のデザイナーを持たないアクティビティの既定の基本アクティビティ デザイナー型です。 この型には、プロパティ グリッドと対話し、色やアイコンの管理などの基本的な側面を構成するデザイン時の機能があります。

<xref:System.Activities.Presentation.ActivityDesigner> では、カスタム アクティビティ デザイナーを開発しやすくする 2 つのヘルパー コントロール <xref:System.Activities.Presentation.WorkflowItemPresenter> と <xref:System.Activities.Presentation.WorkflowItemsPresenter> を使用します。 これらは、子要素のドラッグ アンド ドロップ、その子要素の削除、選択、追加などの一般的な機能を処理します。 では、 <xref:System.Activities.Presentation.WorkflowItemPresenter> "ドロップゾーン" を提供する内の単一の子 UI 要素を使用できます。また、では、 <xref:System.Activities.Presentation.WorkflowItemsPresenter> 子要素の順序付け、移動、削除、追加などの追加機能を含む複数の ui 要素をサポートできます。

カスタムアクティビティデザイナーの実装で強調表示する必要があるストーリーのもう1つの重要な部分は、WPF のデータバインディングを使用してビジュアルの編集をバインドする方法に関するもので、デザイナーでの編集内容のメモリに格納されているインスタンスです。 これは、モデル アイテム ツリーによって実現されます。モデル アイテム ツリーは、変更通知やイベント (状態の変化など) の追跡を実現するためにも使用されます。

ここでは、次の 2 つの手順の概要を説明します。

1. 1 つ目の手順では、他のアクティビティを受け取るドロップ ゾーンを提供する <xref:System.Activities.Presentation.WorkflowItemPresenter> を使用してカスタム アクティビティ デザイナーを作成する方法を説明します。 この手順は、「[カスタム複合デザイナー-Workflow Item プレゼンター](./samples/custom-composite-designers-workflow-item-presenter.md) sample」に基づいています。

2. 2 つ目の手順では、含まれている要素のコレクションを編集するために必要な機能を提供する <xref:System.Activities.Presentation.WorkflowItemsPresenter> を使用してカスタム アクティビティ デザイナーを作成する方法を説明します。 この手順は、「[カスタム複合デザイナー-Workflow Items プレゼンター](./samples/custom-composite-designers-workflow-items-presenter.md) sample」に基づいています。

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a>WorkflowItemPresenter を使用してドロップ ゾーンを含むカスタム アクティビティ デザイナーを作成するには

1. Visual Studio 2010 を起動します。

2. [**ファイル**] メニューの [**新規作成**] をポイントし、[**プロジェクト**] をクリックします。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3. [**インストールされたテンプレート**] ペインで、任意の言語カテゴリから [ **Windows** ] を選択します。

4. [**テンプレート**] ペインで、[ **WPF アプリケーション**] を選択します。

5. [**名前**] ボックスに「」と入力し `UsingWorkflowItemPresenter` ます。

6. [**場所**] ボックスに、プロジェクトを保存するディレクトリを入力するか、[**参照**] をクリックして移動します。

7. [**ソリューション**] ボックスで、既定値をそのまま使用します。

8. **[OK]** をクリックします。

9. **ソリューションエクスプローラー**で*mainwindows .xaml*ファイルを右クリックし、[**削除**] を選択し、[ **Microsoft Visual Studio** ] ダイアログボックスで [ **OK]** をクリックします。

10. **ソリューションエクスプローラー**で [の Workflowitemプレゼンター] プロジェクトを右クリックし、[**追加**]、[**新しい項目...** ] の順に選択します。 [**新しい項目の追加**] ダイアログボックスを表示するには、左側の [**インストールされているテンプレート**] セクションで [ **WPF** ] カテゴリを選択します。

11. [**ウィンドウ (WPF)]** テンプレートを選択し、という名前 `RehostingWFDesigner` を指定して、[**追加**] をクリックします。

12. *Rehostingwfdesigner.xaml*ファイルを開き、次のコードを貼り付けて、アプリケーションの UI を定義します。

    ```xaml
    <Window x:Class=" UsingWorkflowItemPresenter.RehostingWFDesigner"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"
            xmlns:sys="clr-namespace:System;assembly=mscorlib"
            Title="Window1" Height="600" Width="900">
        <Window.Resources>
            <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>
        </Window.Resources>
        <Grid>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="2*"/>
                <ColumnDefinition Width="7*"/>
                <ColumnDefinition Width="3*"/>
            </Grid.ColumnDefinitions>
            <Border Grid.Column="0">
                <sapt:ToolboxControl Name="Toolbox">
                    <sapt:ToolboxCategory CategoryName="Basic">
                        <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.Sequence
                            </sapt:ToolboxItemWrapper.ToolName>
                           </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.WriteLine
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.If
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.While
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                    </sapt:ToolboxCategory>
                </sapt:ToolboxControl>
            </Border>
            <Border Grid.Column="1" Name="DesignerBorder"/>
            <Border Grid.Column="2" Name="PropertyBorder"/>
        </Grid>
    </Window>
    ```

13. アクティビティ デザイナーをアクティビティ タイプと関連付けるには、そのアクティビティ デザイナーをメタデータ ストアを使用して登録する必要があります。 この操作を行うには、`RegisterMetadata` メソッドを `RehostingWFDesigner` クラスに追加します。 `RegisterMetadata` メソッドのスコープで <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> オブジェクトを作成し、<xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> メソッドを呼び出して属性を追加します。 <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> メソッドを呼び出して <xref:System.Activities.Presentation.Metadata.AttributeTable> をメタデータ ストアに追加します。 次のコードには、デザイナーの再ホスト ロジックが含まれています  (メタデータの登録、`SimpleNativeActivity` のツールボックスへの追加、およびワークフローの作成)。 このコードを*RehostingWFDesigner.xaml.cs*ファイルに追加します。

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Presentation.Toolbox;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespace UsingWorkflowItemPresenter
    {
        // Interaction logic for RehostingWFDesigner.xaml
        public partial class RehostingWFDesigner
        {
            public RehostingWFDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();
                // Add custom activity to toolbox.
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

14. ソリューションエクスプローラーで参照ディレクトリを右クリックし、[**参照の追加**] を選択します。 を選択すると、[**参照の追加**] ダイアログボックスが表示されます。

15. [ **.Net** ] タブをクリックし、「system.string」と**いう名前の**アセンブリを見つけて選択し、[ **OK**] をクリックします。

16. 同じ手順で次のアセンブリへの参照を追加します。

    1. System.Data.DataSetExtensions.dll

    2. System.Activities.Presentation.dll

    3. System.ServiceModel.Activities.dll

17. *App.xaml*ファイルを開き、startupuri の値を "rehostingwfdesigner.xaml" に変更します。

18. **ソリューションエクスプローラー**で [の Workflowitemプレゼンター] プロジェクトを右クリックし、[**追加**]、[**新しい項目...** ] の順に選択します。 [**新しい項目の追加**] ダイアログを表示するには、左側の [**インストールされているテンプレート**] セクションで [**ワークフロー** ] カテゴリを選択します。

19. **アクティビティデザイナー**テンプレートを選択し、という名前 `SimpleNativeDesigner` を指定して、[**追加**] をクリックします。

20. *SimpleNativeDesigner*ファイルを開き、次のコードを貼り付けます。 このコードは、<xref:System.Activities.Presentation.ActivityDesigner> をルート要素として使用し、子の型を複合アクティビティ デザイナーに表示できるように、バインディングを使用してデザイナーに <xref:System.Activities.Presentation.WorkflowItemPresenter> を統合する方法を示しています。

    > [!NOTE]
    > <xref:System.Activities.Presentation.ActivityDesigner> のスキーマでは、カスタム アクティビティ デザイナー定義に 1 つの子要素のみを追加できます。ただし、この要素は、`StackPanel`、`Grid` などの複合 UI 要素の可能性があります。

    ```xaml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemPresenter.SimpleNativeDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
        <sap:ActivityDesigner.Resources>
            <DataTemplate x:Key="Collapsed">
                <StackPanel>
                    <TextBlock>This is the collapsed view</TextBlock>
                </StackPanel>
            </DataTemplate>
            <DataTemplate x:Key="Expanded">
                <StackPanel>
                    <TextBlock>Custom Text</TextBlock>
                    <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                            HintText="Please drop an activity here" />
                </StackPanel>
            </DataTemplate>
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
                <Style.Triggers>
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                    </DataTrigger>
                </Style.Triggers>
            </Style>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
        </Grid>
    </sap:ActivityDesigner>
    ```

21. **ソリューションエクスプローラー**で [の Workflowitemプレゼンター] プロジェクトを右クリックし、[**追加**]、[**新しい項目...** ] の順に選択します。 [**新しい項目の追加**] ダイアログを表示するには、左側の [**インストールされているテンプレート**] セクションで [**ワークフロー** ] カテゴリを選択します。

22. **Code アクティビティ**テンプレートを選択し、という名前 `SimpleNativeActivity` を指定して、[**追加**] をクリックします。

23. `SimpleNativeActivity` *SimpleNativeActivity.cs*ファイルに次のコードを入力して、クラスを実装します。

    ```csharp
    using System.Activities;

    namespace UsingWorkflowItemPresenter
    {
        public sealed class SimpleNativeActivity : NativeActivity
        {
            // this property contains an activity that will be scheduled in the execute method
            // the WorkflowItemPresenter in the designer is bound to this to enable editing
            // of the value
            public Activity Body { get; set; }

            protected override void CacheMetadata(NativeActivityMetadata metadata)
            {
               metadata.AddChild(Body);
               base.CacheMetadata(metadata);

            }

            protected override void Execute(NativeActivityContext context)
            {
                context.ScheduleActivity(Body);
            }
        }
    }
    ```

24. [**ビルド**] メニューの [**ソリューションのビルド**] を選択します。

25. [**デバッグ**] メニューの [**デバッグなしで開始**] をクリックして、再ホストされたカスタムデザインウィンドウを開きます。

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a>WorkflowItemsPresenter を使用してカスタム アクティビティ デザイナーを作成するには

1. 2番目のカスタムアクティビティデザイナーの手順は、最初にいくつかの変更を加えたものです。最初に、2つ目のアプリケーションに名前を付け `UsingWorkflowItemsPresenter` ます。 また、このアプリケーションでは新しいカスタム アクティビティを定義しません。

2. キーの違いは、 *Customparalleldesigner .xaml*および*RehostingWFDesigner.xaml.cs*ファイルに含まれています。 次に、UI を定義する*Customparalleldesigner .xaml*ファイルのコードを示します。

    ```xaml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemsPresenter.CustomParallelDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
        <sap:ActivityDesigner.Resources>
            <DataTemplate x:Key="Collapsed">
                <TextBlock>This is the Collapsed View</TextBlock>
            </DataTemplate>
            <DataTemplate x:Key="Expanded">
                <StackPanel>
                    <TextBlock HorizontalAlignment="Center">This is the</TextBlock>
                    <TextBlock HorizontalAlignment="Center">extended view</TextBlock>
                    <sap:WorkflowItemsPresenter HintText="Drop Activities Here"
                                        Items="{Binding Path=ModelItem.Branches}">
                        <sap:WorkflowItemsPresenter.SpacerTemplate>
                            <DataTemplate>
                                <Ellipse Width="10" Height="10" Fill="Black"/>
                            </DataTemplate>
                        </sap:WorkflowItemsPresenter.SpacerTemplate>
                        <sap:WorkflowItemsPresenter.ItemsPanel>
                            <ItemsPanelTemplate>
                                <StackPanel Orientation="Horizontal"/>
                            </ItemsPanelTemplate>
                        </sap:WorkflowItemsPresenter.ItemsPanel>
                    </sap:WorkflowItemsPresenter>
                </StackPanel>
            </DataTemplate>
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
                <Style.Triggers>
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                    </DataTrigger>
                </Style.Triggers>
            </Style>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>
        </Grid>
    </sap:ActivityDesigner>
    ```

3. 再ホストロジックを提供する*RehostingWFDesigner.xaml.cs*ファイルのコードを次に示します。

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespaceUsingWorkflowItemsPresenter
    {
        public partial class RehostingWfDesigner : Window
        {
            public RehostingWfDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

## <a name="see-also"></a>関連項目

- <xref:System.Activities.Presentation.ActivityDesigner>
- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- <xref:System.Activities.Presentation.WorkflowViewElement>
- <xref:System.Activities.Presentation.Model.ModelItem>
- [ワークフロー デザイン操作のカスタマイズ](customizing-the-workflow-design-experience.md)
