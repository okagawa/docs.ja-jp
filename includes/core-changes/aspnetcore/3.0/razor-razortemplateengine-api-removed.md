---
ms.openlocfilehash: 35dd8db243b03e1dfd6311195ec97673cf114877
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032631"
---
### <a name="razor-razortemplateengine-api-removed"></a>Razor: RazorTemplateEngine API が削除されました

[RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2) API が削除され、<xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> に置き換えられました。

ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#25215](https://github.com/dotnet/aspnetcore/issues/25215) を参照してください。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="old-behavior"></a>以前の動作

Razor ファイルのコードを解析し、生成するためにテンプレート エンジンを作成し、使用できます。

#### <a name="new-behavior"></a>新しい動作

Razor ファイルのコードを解析し、生成するために、`RazorProjectEngine` を作成し、`RazorTemplateEngine` と同じ種類の情報を提供できます。 `RazorProjectEngine` からは追加の構成レベルも与えられます。

#### <a name="reason-for-change"></a>変更理由

`RazorTemplateEngine` と既存の実装の結合密度が高すぎました。 Razor の解析および生成パイプラインを正しく構成しようとするとき、この密結合によって問題が増えました。

#### <a name="recommended-action"></a>推奨アクション

`RazorTemplateEngine` ではなく `RazorProjectEngine` を使用します。 次の例を考えてみます。

##### <a name="create-and-configure-the-razorprojectengine"></a>RazorProjectEngine の作成と構成

```csharp
RazorProjectEngine projectEngine =
    RazorProjectEngine.Create(RazorConfiguration.Default,
        RazorProjectFileSystem.Create(@"C:\source\repos\ConsoleApp4\ConsoleApp4"),
        builder =>
        {
            builder.ConfigureClass((document, classNode) =>
            {
                classNode.ClassName = "MyClassName";

                // Can also configure other aspects of the class here.
            });

            // More configuration can go here
        });
```

##### <a name="generate-code-for-a-razor-file"></a>Razor ファイルのコードを生成する

```csharp
RazorProjectItem item = projectEngine.FileSystem.GetItem(
    @"C:\source\repos\ConsoleApp4\ConsoleApp4\Example.cshtml",
    FileKinds.Legacy);
RazorCodeDocument output = projectEngine.Process(item);

// Things available
RazorSyntaxTree syntaxTree = output.GetSyntaxTree();
DocumentIntermediateNode intermediateDocument =
    output.GetDocumentIntermediateNode();
RazorCSharpDocument csharpDocument = output.GetCSharpDocument();
```

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

- [RazorTemplateEngine](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengine?view=aspnetcore-2.2)
- [RazorTemplateEngineOptions](/dotnet/api/microsoft.aspnetcore.razor.language.razortemplateengineoptions?view=aspnetcore-2.2)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngine`
- `T:Microsoft.AspNetCore.Razor.Language.RazorTemplateEngineOptions`

-->
