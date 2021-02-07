---
description: '詳細情報: デザイナーによって XAML ファイルに追加されるビューステートの削除'
title: デザイナーによって XAML ファイルに追加されるビューステートを削除する-WF
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: e6be1e8e4f754085b98f912923ad67cb12893910
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741797"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a>デザイナーによって XAML ファイルに追加されるビューステートを削除する

このサンプルでは、<xref:System.Xaml.XamlWriter> から派生するクラスを作成する方法を示し、XAML ファイルからビュー ステートを削除します。 Windows ワークフローデザイナーは、ビューステートと呼ばれる情報を XAML ドキュメントに書き込みます。 ビュー ステートは、ランタイムでは不必要なレイアウト配置などの、デザイン時に必要な情報を参照します。 ワークフローデザイナーは、編集時にこの情報を XAML ドキュメントに挿入します。 ワークフローデザイナーは、属性を使用してビューステートを XAML ファイルに書き込み `mc:Ignorable` ます。そのため、ランタイムが xaml ファイルを読み込むときに、この情報は読み込まれません。 このサンプルでは、XAML ノードの処理中にそのビューステート情報を削除するクラスを作成する方法を示します。

## <a name="discussion"></a>ディスカッション

このサンプルでは、カスタム ライターを作成する方法を示します。

カスタム XAML ライターをビルドするには、<xref:System.Xaml.XamlWriter> を継承するクラスを作成します。 多くの場合、XAML ライターは入れ子になっているため、"内部" の XAML ライターを追跡します。 これらの "内部" ライターは、XAML ライターの残りのスタックへの参照と考えることができます。これにより、複数のエントリポイントを使用して処理を行い、処理をスタックの残りの部分に委任することができます。

このサンプルには、重要な項目がいくつかあります。 その 1 つとして、書き込まれる項目がデザイナー名前空間からのものであるかどうかの確認が挙げられます。 これにより、ワークフローでデザイナー名前空間の他の型の使用が排除されることに注意してください。

```csharp
static Boolean IsDesignerAttachedProperty(XamlMember xamlMember)
{
    return xamlMember.IsAttachable &&
        xamlMember.PreferredXamlNamespace.Equals(c_sapNamespaceURI, StringComparison.OrdinalIgnoreCase);
}

const String c_sapNamespaceURI = "http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation";

// The next item of interest is the constructor, where the utilization of the inner XAML writer is seen.
public ViewStateCleaningWriter(XamlWriter innerWriter)
{
    this.InnerWriter = innerWriter;
    this.MemberStack = new Stack<XamlMember>();
}

XamlWriter InnerWriter {get; set; }
Stack<XamlMember> MemberStack {get; set; }
```

これにより、ノード ストリームの走査中に使用される XAML メンバーのスタックも作成されます。 このサンプルの残りの作業は、主に `WriteStartMember` メソッドに含まれています。

```csharp
public override void WriteStartMember(XamlMember xamlMember)
{
    MemberStack.Push(xamlMember);

    if (IsDesignerAttachedProperty(xamlMember))
    {
        m_attachedPropertyDepth++;
    }

    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteStartMember(xamlMember);
}
```

後続のメソッドで、まだビューステート コンテナーに含まれているかどうかがチェックされ、含まれている場合は制御が戻り、ノードはライター スタックに渡されません。

```csharp
public override void WriteValue(Object value)
{
    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteValue(value);
}
```

カスタム XAML ライターを使用するには、XAML ライターのスタックでまとめて連結する必要があります。 この使用方法を次のコードに示します。

```csharp
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);
```

## <a name="to-use-this-sample"></a>このサンプルを使用するには

1. Visual Studio 2010 を使用して、ViewStateCleaningWriter ソリューションファイルを開きます。

2. コマンド プロンプトを開き、ViewStageCleaningWriter.exe がビルドされているディレクトリに移動します。

3. Workflow1.xaml ファイルに対して ViewStateCleaningWriter.exe を実行します。

   実行可能ファイルの構文の例を次に示します。

   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```

   これにより \[ 、すべてのビューステート情報が削除された状態で、XAML ファイルがに出力されます。

> [!NOTE]
> <xref:System.Activities.Statements.Sequence> ワークフローでは、多数の仮想化のヒントが削除されます。 その結果、デザイナーは次回の読み込み時にレイアウトを再計算します。 このサンプルを <xref:System.Activities.Statements.Flowchart> に対して使用すると、すべての配置情報および線のルーティング情報が削除され、後続のデザイナーへの読み込み時にすべてのアクティビティが画面の左側に積み上げられます。

## <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a>このサンプルで使用するサンプル XAML ファイルを作成するには

1. Visual Studio 2010 を開きます。

2. 新しいワークフロー コンソール アプリケーションを作成します。

3. いくつかのアクティビティをキャンバスにドラッグ アンド ドロップします。

4. ワークフロー XAML ファイルを保存します。

5. XAML ファイルを調べて、ビューステートの添付プロパティを確認します。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。 このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
