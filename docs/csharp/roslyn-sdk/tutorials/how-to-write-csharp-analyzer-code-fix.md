---
title: 'チュートリアル: 最初のアナライザーとコード修正を作成する'
description: このチュートリアルでは、.NET Compiler SDK (Roslyn API) を使用してアナライザーとコード修正を作成する手順を詳しく説明します。
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: c70fcacc6cb30969e5c69ffd0954ac52e637a915
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100939"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a>チュートリアル: 最初のアナライザーとコード修正を作成する

.NET Compiler Platform SDK には、C# または Visual Basic コードをターゲットとするカスタム警告を作成するために必要なツールが用意されています。 **アナライザー**には、規則違反を認識するコードが含まれています。 **コード修正**には、違反を修正するコードが含まれています。 実装する規則には、コード構造から、コーディング スタイル、名前付け規則などがあります。 .NET Compiler Platform には、開発者がコードを作成するときに分析を実行するためのフレームワークと、コードを修正するためのすべての Visual Studio UI 機能が用意されています。具体的には、エディターに波線を表示する、Visual Studio のエラー一覧を表示する、"電球" の提案を作成する、推奨される修正の豊富なプレビューを表示するなどの機能です。

このチュートリアルでは、Roslyn API を使用して**アナライザー**とそれに付随する**コード修正**の作成について説明します。 アナライザーは、ソース コードの分析を実行し、問題をユーザーに報告する方法の 1 つです。 必要に応じて、アナライザーは、ユーザーのソース コードに対する変更を表すコード修正を提供することもできます。 このチュートリアルでは、`const` 修飾子を使用して宣言できますが、実際は宣言されていないローカル変数宣言を検出するアナライザーを作成します。 付随するコード修正は、それらの宣言を修正して `const` 修飾子を追加します。

## <a name="prerequisites"></a>必須コンポーネント

> [!NOTE]
> 現行の Visual Studio **コード修正付きアナライザー (.NET Standard)** テンプレートには既知のバグが含まれていますが、Visual Studio 2019 バージョン 16.7 で修正されます。 テンプレートのプロジェクトは、次の変更が行われない限り、コンパイルされません。
>
> 1. **[ツール]** 、 **[オプション]** 、 **[NuGet パッケージ マネージャー]** 、 **[パッケージ ソース]** の順に選択します。
>    - プラス記号ボタンを選択すると、新しいソースが追加されます。
>    - **[ソース]** を `https://dotnet.myget.org/F/roslyn-analyzers/api/v3/index.json` に設定し、 **[更新]** を選択します。
> 1. **[ソリューション エクスプローラー]** で **[MakeConst.Vsix]** プロジェクトを右クリックし、 **[プロジェクト ファイルの編集]** を選択します。
>    - `<AssemblyName>` ノードを更新し、`.Visx` サフィックスを追加します。
>      - `<AssemblyName>MakeConst.Vsix</AssemblyName>`
>    - 41 行目の `<ProjectReference>` ノードを更新し、`TargetFramework` の値を変更します。
>      - `<ProjectReference Update="@(ProjectReference)" AdditionalProperties="TargetFramework=netstandard2.0" />`
> 1. *[MakeConst.Test]* プロジェクトで *MakeConstUnitTests.cs* ファイルを更新します。
>    - 9 行目を次のように変更します。名前空間の変更に注目してください。
>      - `using Verify = Microsoft.CodeAnalysis.CSharp.Testing.MSTest.CodeFixVerifier<`
>    - 24 行目を次のメソッドに変更します。
>      - `await Verify.VerifyAnalyzerAsync(test);`
>    - 62 行目を次のメソッドに変更します。
>      - `await Verify.VerifyCodeFixAsync(test, expected, fixtest);`

- [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [Visual Studio 2019](https://www.visualstudio.com/downloads)

Visual Studio インストーラーで **.NET Compiler Platform SDK** をインストールする必要があります。

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

アナライザーの作成と検証にはいくつかの手順があります。

1. ソリューションを作成します。
1. アナライザーの名前と説明を登録します。
1. アナライザーの警告と推奨事項を報告します。
1. 推奨事項を受け取るコード修正を実装します。
1. 単体テストで分析を改善します。

## <a name="explore-the-analyzer-template"></a>アナライザー テンプレートを調べる

アナライザーは、ローカル定数に変換できるローカル変数宣言をユーザーに報告します。 次に例を示します。

```csharp
int x = 0;
Console.WriteLine(x);
```

上記のコードでは、`x` には定数値が割り当てられており、変更されることはありません。 これは `const` 修飾子を使用して宣言できます。

```csharp
const int x = 0;
Console.WriteLine(x);
```

変数を定数にすることができるかどうかを判断するために、構文解析、初期化子式の定数分析、および変数に書き込まれないというデータフロー分析が必要です。 .NET Compiler Platform には、この分析を簡単に実行できる API が用意されています。 最初の手順は、新しい C# の**コード修正を含むアナライザー** プロジェクトを作成することです。

- Visual Studio で、 **[ファイル] > [新規] > [プロジェクト]** の順に選択して、[新しいプロジェクト] ダイアログを表示します。
- **[Visual C#] > [Extensibility]** で、 **[Analyzer with code fix (.NET Standard)]\(コード修正付きアナライザー (.NET Standard)\)** を選択します。
- プロジェクトに「**MakeConst**」という名前を付けて、[OK] をクリックします。

コード修正テンプレート付きアナライザー テンプレートを使用すると、アナライザーとコード修正を含むプロジェクト、単体テスト プロジェクト、VSIX プロジェクトという 3 つのプロジェクトが作成されます。 既定のスタートアップ プロジェクトは VSIX プロジェクトです。 <kbd>F5</kbd> キーを押して、VSIX プロジェクトを開始します。 これにより、新しいアナライザーが読み込まれた Visual Studio の 2 つ目のインスタンスが開始されます。

> [!TIP]
> アナライザーを実行するときは、Visual Studio の 2 つ目のコピーを開始します。 この 2 つ目のコピーは、別のレジストリ ハイブを使用して設定を保存します。 これにより、Visual Studio の 2 つのコピーのビジュアル設定を区別することができます。 Visual Studio の実験的な実行のために、別のテーマを選択することができます。 また、設定のローミングや、Visual Studio アカウントへのログインには、Visual Studio の実験的な実行が使用されません。 そのため、設定を分けておくことができます。

開始した 2 つ目の Visual Studio インスタンスで、新しい C# コンソール アプリケーション プロジェクトを作成します (.NET Core または .NET Framework プロジェクトが動作し、アナライザーはソース レベルで動作します)。波線の下線が表示されているトークンにマウス カーソルを移動すると、アナライザーに設定されている警告テキストが表示されます。

テンプレートを使用すると、次の図のように、型名が小文字の個々の型宣言に対して警告を報告するアナライザーが作成されます。

![警告を報告するアナライザー](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

また、テンプレートには、小文字を含むすべての型名をすべて大文字に変更するコード修正も用意されています。 警告が表示された電球をクリックすると、推奨される変更が表示されます。 推奨される変更を受け入れると、型の名前と、ソリューション内のその型に対するすべての参照が更新されます。 最初のアナライザーの動作を確認したら、2 つ目の Visual Studio インスタンスを閉じ、アナライザー プロジェクトに戻ります。

アナライザーのすべての変更をテストするために、Visual Studio の 2 つ目のコピーを開始して、新しいコードを作成する必要はありません。 このテンプレートを使用すると、単体テスト プロジェクトも自動的に作成されます。 このプロジェクトには 2 つのテストが含まれています。 `TestMethod1` では、診断をトリガーせずにコードを分析するテストの一般的な形式が表示されます。 `TestMethod2` では、診断をトリガーするテストの形式が表示され、推奨されたコード修正が適用されます。 アナライザーとコード修正をビルドするときに、異なるコード構造のテストを作成して作業を検証します。 アナライザーの単体テストは、Visual Studio を使用して対話的にテストするよりもはるかに簡単です。

> [!TIP]
> アナライザーの単体テストは、アナライザーをトリガーするべきコード構造とトリガーするべきではないコード構造を知りたいときに最適なツールです。 Visual Studio のもう 1 つのコピーにアナライザーを読み込むことは、まだ検討していない可能性のあるコンストラクトを探索して見つけるために最適なツールです。

## <a name="create-analyzer-registrations"></a>アナライザーの登録を作成する

このテンプレートを使用すると、**MakeConstAnalyzer.cs** ファイルに初期の `DiagnosticAnalyzer` クラスが作成されます。 この初期のアナライザーは、あらゆるアナライザーが持つ 2 つの重要な特性を示しています。

- すべての診断アナライザーは、動作する言語を記述する `[DiagnosticAnalyzer]` 属性を提供する必要があります。
- すべての診断アナライザーは、<xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> クラスから派生する必要があります。

このテンプレートは、アナライザーの一部である基本機能も示しています。

1. アクションを登録します。 アクションは、アナライザーをトリガーしてコード違反を調べるコードの変更を表します。 Visual Studio で、登録済みのアクションと一致するコード編集が検出されると、アナライザーの登録済みメソッドが呼び出されます。
1. 診断を作成します。 アナライザーで違反を検出されると、違反をユーザーに通知するために Visual Studio で使用される診断オブジェクトが作成されます。

<xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> メソッドのオーバーライドでアクションを登録します。 このチュートリアルでは、**構文ノード**にアクセスしてローカル宣言を探し、定数値を持つものを調べます。 宣言が定数であれば、アナライザーによって診断が作成され、報告されます。

最初の手順は、登録定数が "Make Const" アナライザーを示すように、登録定数と `Initialize` メソッドを更新することです。 ほとんどの文字列定数は、文字列リソース ファイルで定義されています。 ローカリゼーションを容易にするには、この手法に従うことをお勧めします。 **MakeConst** アナライザー プロジェクト用に **Resources.resx** ファイルを開きます。 これでリソース エディターが表示されます。 文字列リソースを次のように更新します。

- `AnalyzerTitle` を "変数を定数に変更できる" に変更します。
- `AnalyzerMessageFormat` を "定数に変更できる" に変更します。
- `AnalyzerDescription` を "定数にする" に変更します。

また、 **[アクセス修飾子]** ドロップダウンを `public` に変更します。 こうすることで、単体テストでこれらの定数を簡単に使用できるようになります。 完了すると、次の図のようにリソース エディターが表示されます。

![文字列リソースを更新する](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

残りの変更はアナライザー ファイル内にあります。 Visual Studio で **MakeConstAnalyzer.cs** を開きます。 登録済みアクションを、シンボル対して動作するものから構文に対して動作するものに変更します。 `MakeConstAnalyzerAnalyzer.Initialize` メソッドで、シンボルにアクションを登録する行を見つけます。

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

これを次の行で置き換えます。

[!code-csharp[Register the node action](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

この変更後は、`AnalyzeSymbol` メソッドを削除できます。 このアナライザーでは、<xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> ステートメントではなく <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType> ステートメントが検査されます。 `AnalyzeNode` に赤い波線が表示されていることに注意してください。 追加したコードは、宣言されていない `AnalyzeNode` メソッドを参照しています。 次のコードを使用してそのメソッドを宣言します。

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

次のコードに示すように、**MakeConstAnalyzer.cs**  の `Category` を "Usage" に変更します。

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a>定数の可能性があるローカル宣言を見つける

次は `AnalyzeNode` メソッドの最初のバージョンを作成してみましょう。 次のコードのように、`const` の可能性がありますが実際はそうではない単一のローカル宣言を探します。

```csharp
int x = 0;
Console.WriteLine(x);
```

最初の手順は、ローカル宣言を見つけることです。 **MakeConstAnalyzer.cs** の `AnalyzeNode` に次のコードを追加します。

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

アナライザーにローカル宣言 (ローカル宣言のみ) の変更が登録されているため、このキャストは常に成功します。 他のノードの種類では `AnalyzeNode` メソッドへの呼び出しがトリガーされません。 次に、`const` 修飾子の宣言を確認します。 見つかったら、すぐに戻ります。 次のコードでは、ローカル宣言の `const` 修飾子を探します。

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

最後に、変数を `const` にすることができることを確認する必要があります。 つまり、初期化後に決して割り当てられないことを確認します。

<xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext> を使用していくつかのセマンティック解析を実行します。 `context` 引数を使用して、ローカル変数の宣言を `const` にすることができるかどうかを判断します。 <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> は、単一のソース ファイル内のすべてのセマンティック情報を表します。 詳細については、[セマンティック モデル](../work-with-semantics.md)に関する記事を参照してください。 <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> を使用して、ローカル宣言ステートメントでデータ フロー分析を実行します。 次に、このデータ フロー分析の結果を使用して、ローカル変数が他の場所の新しい値で上書きされないようにします。 変数の <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> 拡張メソッドを呼び出して変数の <xref:Microsoft.CodeAnalysis.ILocalSymbol> を取得し、データ フロー分析の <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> コレクションに含まれていないことを確認します。 `AnalyzeNode` メソッドの末尾に次のコードを追加します。

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

この追加したコードで、変数は変更されなくなります。そのため、`const` にすることができます。 それでは診断を呼び出してみましょう。 `AnalyzeNode` の最後の行に次のコードを追加します。

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

<kbd>F5</kbd> キーを押してアナライザーを実行して、進行状況を確認できます。 以前に作成したコンソール アプリケーションを読み込み、次のテスト コードを追加することができます。

```csharp
int x = 0;
Console.WriteLine(x);
```

電球が表示され、アナライザーから診断が報告されます。 ただし、電球には、テンプレートで生成されたコード修正が使用されているので、大文字にすることができることがわかります。 次のセクションでは、コード修正の記述方法について説明します。

## <a name="write-the-code-fix"></a>コード修正を記述する

アナライザーで、1 つまたは複数のコード修正が表示される可能性があります。 コード修正では、報告された問題を解決する編集が定義されます。 作成したアナライザーに、const キーワードを挿入するコード修正を用意することができます。

```csharp
const int x = 0;
Console.WriteLine(x);
```

エディターの電球の UI からユーザーが選択すると、Visual Studio によってコードが変更されます。

テンプレートによって追加された **MakeConstCodeFixProvider.cs** ファイルを開きます。  このコード修正は、診断アナライザーによって生成された診断 ID に既に関連付けられていますが、まだ適切なコード変換が実装されていません。 まず、テンプレート コードの一部を削除する必要があります。 タイトルの文字列を "定数にする" に変更します。

[!code-csharp[Update the CodeFix title](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

次に `MakeUppercaseAsync` メソッドを削除します これで適用されなくなります。

すべてのコード修正プロバイダーは <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider> から派生します。 これらはすべて <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> をオーバーライドし、使用できるコード修正を報告します。 `RegisterCodeFixesAsync` で、診断に合わせて、次のように検索している先祖ノードの種類を <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> に変更します。

[!code-csharp[Find local declaration node](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

次に、最後の行を変更してコード修正を登録します。 この修正で、既存の宣言に `const` 修飾子を追加した結果の新しいドキュメントが作成されます。

[!code-csharp[Register the new code fix](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

シンボル `MakeConstAsync` に追加したコードに、赤い波線が表示されている点に注目してください。 次のコードのように、`MakeConstAsync` の宣言を追加します。

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

新しい `MakeConstAsync` メソッドによって、ユーザーのソース ファイルを表す <xref:Microsoft.CodeAnalysis.Document> は、`const` 宣言を含む新しい <xref:Microsoft.CodeAnalysis.Document> に変換されます。

宣言ステートメントの前に挿入される新しい `const` キーワード トークンを作成します。 先頭に trivia があれば、まず宣言ステートメントの最初のトークンから削除し、それを `const` トークンにアタッチします。 `MakeConstAsync` メソッドに次のコードを追加します。

[!code-csharp[Create a new const keyword token](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

次に、以下のコードを使用して宣言に `const` トークンを追加します。

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

次に、C# の書式設定規則に合わせて新しい宣言の書式を設定します。 既存のコードに合わせて変更の書式を設定すると、エクスペリエンスが向上します。 既存のコードの直後に次のステートメントを追加します。

[!code-csharp[Format the new declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

このコード用に新しい名前空間が必要です。 次の `using` ディレクティブをファイルの先頭に追加します。

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

最後の手順は編集です。 このプロセスには 3 つの手順があります。

1. 既存のドキュメントのハンドルを取得する。
1. 既存の宣言を新しい宣言で置き換えて、新しいドキュメントを作成する。
1. 新しいドキュメントを返す。

`MakeConstAsync` メソッドの末尾に次のコードを追加します。

[!code-csharp[replace the declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

コード修正を試す準備が整いました。  <kbd>F5</kbd> キーを押して、Visual Studio の 2 つ目のインスタンスでアナライザー プロジェクトを実行します。 2 つ目の Visual Studio インスタンスで、新しい C# コンソール アプリケーション プロジェクトを作成し、定数値を使用して初期化されたローカル変数宣言をいくつか Main メソッドに追加します。 次のように警告として報告されることがわかります。

![const 警告を生成できる](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

ここでは、さまざまな作業を行いました。 `const` にすることができる宣言には、波線が表示されています。 ただし、まだするべきことがあります。 これは、`i` で始まる宣言に `const` を追加し、次に `j` を追加し、最後に `k` を追加して改善することができます。 ただし、`k` で始まる `const` 修飾子を異なる順序で追加すると、アナライザーによってエラーが生成されます。`i` と `j` の両方が既に `const` でなければ、`k` を `const` と宣言できません。 変数を宣言して初期化できるさまざまな方法を確実に処理できるように、さらに分析を行う必要があります。

## <a name="build-data-driven-tests"></a>データ駆動型テストをビルドする

アナライザーとコード修正は、const にすることができる単一の宣言という単純なケースで動作します。 この実装によって間違いが発生する可能性のある宣言ステートメントは数多くあります。 このようなケースには、テンプレートによって作成される単体テスト ライブラリを使用して対処します。 これは、Visual Studio の 2 つ目のコピーを繰り返し開くよりもはるかに高速です。

単体テスト プロジェクトで **MakeConstUnitTests.cs** ファイルを開きます。 テンプレートによって、アナライザーとコード修正の単体テスト用に 2 つの共通パターンに従う 2 つのテストが作成されています。 `TestMethod1` は、診断を報告すべきではないときに、アナライザーから診断が報告されないようにするテストのパターンを示します。 `TestMethod2` は、診断を報告し、コード修正を実行するためのパターンを示します。

アナライザーのほぼすべてのテストのコードは、この 2 つのパターンのいずれかに従います。 1 つ目の手順では、これらのテストをデータ駆動型テストとして修正することができます。 次に、さまざまなテスト入力を表す新しい文字列定数を追加することで、新しいテストを簡単に作成できます。

効率化するには、1 つ目の手順を 2 つのテストをデータ駆動型テストにリファクターします。 すると、必要な作業は、新しいテストのたびに、いくつかの文字列定数を定義するだけになります。 リファクター時に、両方のメソッドをわかりやすい名前に変更します。 診断が呼び出されないように、`TestMethod1` をこのテストに置き換えます。

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

診断で警告がトリガーされないようにするコード フラグメントすることで、このテスト用に新しいデータ行を作成することができます。 ソース コード フラグメントに対してトリガーされる診断がない場合、`VerifyCSharpDiagnostic` のこのオーバーロードは成功します。

次に、`TestMethod2` をこのテストに置き換えて、診断を呼び出し、ソース コード フラグメントに対してコード修正を適用するようにします。

```csharp
[DataTestMethod]
[DataRow(LocalIntCouldBeConstant, LocalIntCouldBeConstantFixed, 10, 13)]
public void WhenDiagnosticIsRaisedFixUpdatesCode(
    string test,
    string fixTest,
    int line,
    int column)
{
    var expected = new DiagnosticResult
    {
        Id = MakeConstAnalyzer.DiagnosticId,
        Message = new LocalizableResourceString(nameof(MakeConst.Resources.AnalyzerMessageFormat), MakeConst.Resources.ResourceManager, typeof(MakeConst.Resources)).ToString(),
        Severity = DiagnosticSeverity.Warning,
        Locations =
            new[] {
                    new DiagnosticResultLocation("Test0.cs", line, column)
                }
    };

    VerifyCSharpDiagnostic(test, expected);

    VerifyCSharpFix(test, fixTest);
}
```

また、前のコードでは、想定される診断結果を構築する変更をいくつかコードに加えました。 これには `MakeConst` アナライザーに登録されたパブリック定数が使用されます。 さらに、入力ソースと修正済みソース用に 2 つの文字列定数が使用されます。 `UnitTest` クラスに次の文字列定数を追加します。

[!code-csharp[string constants for fix test](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

これらの 2 つのテストを実行して、合格することを確認します。 Visual Studio で、 **[テスト]**  >  **[Windows]**  >  **[テスト エクスプローラー]** の順に選択して、**テスト エクスプローラー**を開きます。 次に、 **[すべて実行]** リンクを選択します。

## <a name="create-tests-for-valid-declarations"></a>有効な宣言のテストを作成する

一般的な規則として、アナライザーはできるだけ早く終了し、最低限の作業を行う必要があります。 ユーザーがコードを編集すると、Visual Studio では登録済みのアナライザーが呼び出されます。 応答性は重要な要件です。 診断を呼び出すべきではないコードのテストケースがいくつかあります。 このアナライザーは、このようなテストのうち、初期化後に変数が割り当てられるケースのテストを既に処理しています。 そのケースを表すために、テストに次の文字列定数を追加します。

[!code-csharp[variable assigned](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

次に、以下のスニペットに示すように、このテストのデータ行を追加します。

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

このテストも合格します。 次に、まだ処理していない条件の定数を追加します。

- 既に const なので、既に `const` である宣言:

   [!code-csharp[already const declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- 使用する価値がないため、初期化子がない宣言:

   [!code-csharp[declarations that have no initializer](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- コンパイル時の定数にすることはできないため、初期化子が定数ではない宣言:

   [!code-csharp[declarations where the initializer isn't const](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

C# は複数の宣言を 1 つのステートメントとして許可するので、さらに複雑になる可能性があります。 次のテスト ケース文字列定数を考えてみましょう。

[!code-csharp[multiple initializers](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

変数 `i` は定数にすることができますが、変数 `j` はできません。 そのため、このステートメントを const 宣言にすることはできません。 これらすべてのテストについて `DataRow` 宣言を追加します。

```csharp
[DataTestMethod]
[DataRow(""),
    DataRow(VariableAssigned),
    DataRow(AlreadyConst),
    DataRow(NoInitializer),
    DataRow(InitializerNotConstant),
    DataRow(MultipleInitializers)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

テストをもう一度実行すると、これらの新しいテスト ケースが失敗することがわかります。

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a>正しい宣言を無視するようにアナライザーを更新する

アナライザーの `AnalyzeNode` メソッドにいくつか拡張を追加して、これらの条件に一致するコードをフィルター処理する必要があります。 これらはすべて関連する条件なので、同様の変更でこれらすべての条件を修正します。 `AnalyzeNode` に次の変更を加えます。

- セマンティック分析では、単一の変数宣言を調査しました。 このコードは、同じステートメントで宣言されたすべての変数を調査する `foreach` ループ内に配置する必要があります。
- 宣言された各変数には初期化子が必要です。
- 宣言された各変数の初期化子は、コンパイル時定数にする必要があります。

`AnalyzeNode` メソッドで、元のセマンティック分析を置き換えます。

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

次のコード スニペットのようにします。

```csharp
// Ensure that all variables in the local declaration have initializers that
// are assigned with constant values.
foreach (var variable in localDeclaration.Declaration.Variables)
{
    var initializer = variable.Initializer;
    if (initializer == null)
    {
        return;
    }

    var constantValue = context.SemanticModel.GetConstantValue(initializer.Value);
    if (!constantValue.HasValue)
    {
        return;
    }
}

// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

foreach (var variable in localDeclaration.Declaration.Variables)
{
    // Retrieve the local symbol for each variable in the local declaration
    // and ensure that it is not written outside of the data flow analysis region.
    var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
    if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
    {
        return;
    }
}
```

最初の `foreach` ループで、構文解析を使用して各変数宣言を調査します。 最初の検査で、変数に初期化子があることを確認します。 2 つ目の検査で、初期化子が定数であることを確認します。 2 つ目のループには、元のセマンティック分析があります。 セマンティック検査は、パフォーマンスに大きな影響があるため、別のループに配置されています。 テストをもう一度実行すると、すべてが合格になるはずです。

## <a name="add-the-final-polish"></a>最後の仕上げを加える

完了までもう少しです。 アナライザーが処理できる条件がまだいくつかあります。 Visual Studio では、ユーザーがコードを記述しているときにアナライザーが呼び出されます。 コンパイルされないコードに対してアナライザーが呼び出されることはよくあります。 診断アナライザーの `AnalyzeNode` メソッドは、定数値を変数型に変換できるかどうかを検査しません。 そのため、現在の実装では、int i = "abc" のような正しくない宣言でもそのままローカル定数に変換されます。 このような条件に対して次のソース文字列定数を追加します。

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

また、参照型が正しく処理されません。 参照型に使用できる唯一の定数値は、文字列リテラルを許可する <xref:System.String?displayProperty=nameWithType> の場合を除き、`null` です。 つまり、`const string s = "abc"` は有効ですが、`const object s = "abc"` は有効ではありません。 このコード スニペットで、次の条件を検証します。

[!code-csharp[Reference types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

さらに徹底するには、文字列の定数宣言を作成できるように別のテストを追加します。 次のスニペットでは、診断を呼び出すコードと、修正が適用された後のコードの両方を定義しています。

[!code-csharp[string reference types raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

最後に、変数が `var` キーワードで宣言されている場合、コード修正で適切な処理が実行されず、C# 言語でサポートされていない `const var` 宣言が生成されます。 このバグを修正するには、コード修正で `var` キーワードを推定型の名前に置き換える必要があります。

[!code-csharp[var references need to use the inferred types](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

これらの変更で、両方のテストのデータ行の宣言が更新されます。 次のコードは、すべてのデータ行の属性を使用したこれらのテストを示しています。

[!code-csharp[The finished tests](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

幸いにも、上記のすべてのバグは、ここで学んだテクニックを使って解決できます。

最初のバグを修正するには、まず **DiagnosticAnalyzer.cs** を開き、各ローカル宣言の初期化子が検査される foreach ループを見つけて、それらに定数値が割り当てられていることを確認します。 最初の foreach ループの_直前_に `context.SemanticModel.GetTypeInfo()` を呼び出し、宣言されたローカル宣言の型に関する詳細情報を取得します。

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

次に、`foreach` ループ内に、各初期化子が変数型に変換できることを確認します。 初期化子が定数であることを確認したら、次の検査を追加します。

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

次の変更は、最後の変更に基づいています。 最初の foreach ループの中かっこの前に、定数が文字列または null の場合にローカル宣言の型を検査する次のコードを追加します。

```csharp
// Special cases:
//  * If the constant value is a string, the type of the local declaration
//    must be System.String.
//  * If the constant value is null, the type of the local declaration must
//    be a reference type.
if (constantValue.Value is string)
{
    if (variableType.SpecialType != SpecialType.System_String)
    {
        return;
    }
}
else if (variableType.IsReferenceType && constantValue.Value != null)
{
    return;
}
```

var' キーワードを正しい型名に置き換えるには、コード修正プロバイダーに少しコードを追加する必要があります。 **CodeFixProvider.cs** に戻ります。 追加するコードで、次の手順が実行されます。

- 宣言が `var` 宣言かどうかを検査し、その場合は次の処理を実行します。
- 推定型の新しい型を作成します。
- 型宣言がエイリアスでないことを確認します。 その場合は、`const var` を宣言することができます。
- `var` がこのプログラムの型名でないことを確認します (その場合、`const var` は有効です)。
- 完全な型名を簡略化する

多数のコードが必要なようですが、 そうではありません。 `newLocal` を宣言し、初期化する行を次のコードに置き換えます。 `newModifiers` の初期化直後に配置します。

[!code-csharp[Replace Var designations](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<xref:Microsoft.CodeAnalysis.Simplification.Simplifier> 型を使用するには、1 つの `using` ディレクティブを追加する必要があります。

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

テストを実行します。テストはすべて合格するはずです。 完成したアナライザーを実行してみてください。 <kbd>Ctrl + F5</kbd> キーを押して Roslyn Preview 拡張機能が読み込まれた Visual Studio の 2 つ目のインスタンスでアナライザー プロジェクトを実行します。

- 2 つ目の Visual Studio インスタンスで、新しい C# コンソール アプリケーション プロジェクトを作成し、`int x = "abc";` を Main メソッドに追加します。 最初のバグ修正のおかげで、このローカル変数宣言について警告は報告されません (ただし、想定どおりコンパイラ エラーが発生します)。
- 次に、Main メソッドに `object s = "abc";` を追加します。 2 つ目のバグ修正のおかげで、警告は報告されません。
- 最後に、`var` キーワードを使用する別のローカル変数を追加します。 警告が報告され、左側の下部に推奨が表示されます。
- 波線にエディターのカレットを移動し、<kbd>Ctrl +</kbd> キーを押します。 推奨されたコード修正が表示されます。 コード修正を選択して、var' キーワードが正しく処理されていることを確認します。

最後に、次のコードを追加します。

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

これらの変更の後は、最初の 2 つの変数にのみ赤い波線が表示されます。 `i` と `j` の両方に `const` を追加すると、`const` になる可能性があるので、`k` で新しい警告を受け取ります。

おめでとうございます! ここでは最初の .NET Compiler Platform 拡張機能を作成しました。これは、その場でコード分析を実行し、問題を検出してそれを修正する簡単な修正案を提供する拡張機能です。 この過程で、.NET Compiler Platform SDK (Roslyn API) に含まれる多くのコード API を学びました。 サンプル GitHub リポジトリの[完成したサンプル](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst)に対して作業を検査することができます。

## <a name="other-resources"></a>その他のリソース

- [構文解析の概要](../get-started/syntax-analysis.md)
- [セマンティック解析の概要](../get-started/semantic-analysis.md)
