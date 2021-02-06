---
description: 詳細については、.NET Framework 4.5 での外部化 Policy アクティビティに関するページを参照してください。
title: .NET Framework 4.5 の外部化されたポリシー アクティビティ
ms.date: 03/30/2017
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
ms.openlocfilehash: 52dad208aacf2993acffa605b896c14c0a906d4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631217"
---
# <a name="externalized-policy-activity-in-net-framework-45"></a>.NET Framework 4.5 の外部化されたポリシー アクティビティ

このサンプルでは、 <xref:System.Workflow.Activities.Rules.RuleSet> [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] wf 3.5 に付属しているルールエンジンを使用して、ExternalizedPolicy4 アクティビティが WINDOWS WORKFLOW FOUNDATION (wf 4.5) の既存の .NET Framework 3.5 WINDOWS WORKFLOW FOUNDATION (wf 3.5) オブジェクトを直接実行できるようにする方法を示します。 このアクティビティを使用すると、既存の WF 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> を開いて実行できます。 Windows Workflow Foundation の一部として含まれる WF 3.5 ルールエンジンの詳細については、「 [Windows Workflow Foundation ルールエンジンの概要](/previous-versions/dotnet/articles/aa480193(v=msdn.10))」を参照してください。 のへの規則の移行の詳細については [!INCLUDE[wf1](../../../../includes/wf1-md.md)] [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] 、移行に関する [ガイダンス](../migration-guidance.md)を参照してください。

## <a name="projects-in-this-sample"></a>このサンプルのプロジェクト

|プロジェクト名|説明|メイン ファイル|
|-|-|-|
|ExternalizedPolicy4|ExternalizedPolicy4 アクティビティとその WF 4.5 デザイナーが含まれます。|**ExternalizedPolicy4.cs**: アクティビティ定義。<br /><br /> **ExternalizedPolicy4Designer**: ExternalizedPolicy4 アクティビティのカスタムデザイナー。 WF 3.5 ルール エンジンからルール エディター (<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>) を使用します。|
|ImperativeCodeClientSample|命令型 C# コードで、ExternalizedPolicy4 アプリケーションを使用してワークフローを構成および実行するサンプル クライアント アプリケーションです (デザイナーは不使用)。|**Applydiscount。ルール**: ルールの定義を含むファイル。 [!INCLUDE[wf1](../../../../includes/wf1-md.md)]<br /><br /> **Order.cs**: 顧客の注文を表す型。 ルールはこの型のオブジェクトに適用されます。<br /><br /> **Program.cs**: Policy4 アクティビティを持つワークフローを構成および実行して、applydiscount で定義されたルールを適用します。ルールオブジェクトのインスタンスにルールを適用します。<br /><br /> App.config: ルール ファイルのパスが記述された構成ファイルです。|
|DesignerClientSample|[!INCLUDE[wf1](../../../../includes/wf1-md.md)] デザイナーで、ExternalPolicy4 アプリケーションを使用してワークフローを構成および実行するサンプル クライアント アプリケーションです。|**Sequence1**: Policy4 アクティビティを使用してルールの評価を実行するシーケンシャルワークフローです。<br /><br /> **Program.cs**: Sequence1 で定義されているワークフローのインスタンスを実行します。|

## <a name="the-externalizedpolicy4-activity"></a>ExternalizedPolicy4 アクティビティ

ExternalizedPolicy4 アクティビティは、WF 4.5 のワークフロー内で WF 3.5 <xref:System.Activities.NativeActivity> オブジェクトを実行できるようにする <xref:System.Workflow.Activities.Rules.RuleSet> です。 次のコード例は、このアクティビティのパブリック オブジェクト モデルの簡略化された定義です。

```csharp
public class ExternalizedPolicy4Activity<TResult>: CodeActivity
{
    public string RulesFilePath

    public string RuleSetName

    [RequiredArgument]
    public InArgument<T> TargetObject

    [RequiredArgument]
    public OutArgument<T> ResultObject

    public OutArgument<ValidationErrorCollection> ValidationErrors
}
```

|プロパティ|説明|
|-|-|
|RuleSetFilePath|アクティビティが実行されるときに評価される .NET Framework 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> ファイルのパスです。|
|RuleSetName|.rules ファイル内で使用される <xref:System.Workflow.Activities.Rules.RuleSet> の名前です。|
|TargetObject|<xref:System.Workflow.Activities.Rules.Rule> の <xref:System.Workflow.Activities.Rules.RuleSet> オブジェクトを評価する対象のオブジェクトです。|
|ResultObject|ルールが適用された後の結果として得られるオブジェクトです (たとえば、ルールが Input 引数に対して適用され、結果が Result 引数に格納されます)。|
|ValidationError|実行前に対象オブジェクトに対して <xref:System.Workflow.Activities.Rules.RuleSet> を検証するときに、WF 3.5 ルール エンジンから返される検証エラーのリストです。|

## <a name="externalizedpolicy4-activity-designer"></a>ExternalizedPolicy4 アクティビティ デザイナー

ExternalizedPolicy4 デザイナーを使用すると、コードを記述せずに、既存の RuleSet を使用するようにアクティビティを構成できます。 .rules ファイルのパスを設定し、使用する <xref:System.Workflow.Activities.Rules.RuleSet> の名前を指定するだけです。 また、<xref:System.Workflow.Activities.Rules.RuleSet> を変更することもできます。 ソリューションをビルドすると、Microsoft.Samples.Activities.Rules セクションのツールボックス内からこのデザイナーを使用できるようになります。 このデザイナーでは、.rules ファイルと <xref:System.Workflow.Activities.Rules.RuleSet> を選択できます。 [ **ルールセットの編集** ] ボタンをクリックすると、WF 3.5 <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog> が表示されます。 このダイアログはホストを変更した WF 3.5 ルール エディターであり、ExternalizedPolicy4 アクティビティで実行するルールを表示および編集するために使用します。

## <a name="policy4-and-externalpolicy4"></a>Policy4 と ExternalPolicy4

ポリシーアクティビティを使用すると、WF 4.5 ワークフローで .NET Framework 3.5 のルールセットを作成して実行できます。 <xref:System.Workflow.Activities.Rules.RuleSet> は、Policy4 アクティビティの XAML 定義でインラインでシリアル化されます。 ExternalizedPolicy4 サンプルでは、既存の外部 <xref:System.Workflow.Activities.Rules.RuleSet> (.rules ファイル内に格納) を使用する方法を示します。

## <a name="use-this-sample"></a>このサンプルを使用する

このサンプルを実行するのに特別な設定は必要ありません。 Visual Studio でソリューションを開き、 **F5** キーを押してアプリケーションを実行します。

このサンプルには、ImperativeCodeClientSample と DesignerClientSample の 2 つのクライアント アプリケーションがあります。 ImperativeCodeClientSample クライアントは、C# 命令型コードを使用して ExternalizedPolicy4 アクティビティを構成および実行する方法を示します。 DesignerClientSample は、デザイナーを使用して ExternalizedPolicy4 アクティビティを構成および実行する方法を示します。

### <a name="run-the-imperativecodeclientsample-application"></a>ImperativeCodeClientSample アプリケーションを実行する

1. Visual Studio を使用して、 *policy4sample.sln* ソリューションファイルを開きます。

2. **ソリューションエクスプローラー** で、 **ImperativeCodeClientSample** プロジェクトを右クリックし、[**スタートアッププロジェクトに設定**] を選択します。

3. プロジェクトを実行するには、 **Ctrl** + **F5** キーを押します。

### <a name="run-the-designerclientsample-application"></a>デザイナ Clientsample アプリケーションを実行する

1. Visual Studio を使用して、 *policy4sample.sln* ソリューションファイルを開きます。

2. **ソリューションエクスプローラー** で、**デザイナ clientsample** プロジェクトを右クリックし、[**スタートアッププロジェクトに設定**] を選択します。

3. **Ctrl** + **Shift** + **B** キーを押して、プロジェクトをコンパイルします。

4. **Ctrl** + **F5** キーを押してプロジェクトを実行します。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。
>
> このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`
