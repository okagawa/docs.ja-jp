---
title: コード分析の警告を表示しない
description: .NET コード分析の違反を抑制するためのさまざまな方法について説明します。
ms.date: 01/28/2021
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- code analysis, suppress warnings
- suppress code analysis warnings
ms.openlocfilehash: b08e93089975a59fabfeb0daaf6a2a6454b2c7e8
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99217263"
---
# <a name="how-to-suppress-code-analysis-warnings"></a>コード分析の警告を非表示にする方法

この記事では、.NET アプリのビルド時にコード分析からの警告を抑制するためのさまざまな方法について説明します。

> [!TIP]
> 開発環境として Visual Studio を使用している場合、 *電球* メニューには、警告を非表示にするコードを生成するオプションが用意されています。 詳細については、「 [違反の抑制](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)」を参照してください。

## <a name="disable-the-rule"></a>ルールを無効にする

警告の原因となっているコード分析規則を無効にすると、ファイルまたはプロジェクト全体の規則が無効になります (使用する [構成ファイル](configuration-files.md) のスコープによって異なります)。 ルールを無効にするには、構成ファイルで重要度をに設定し `none` ます。

```ini
[*.{cs,vb}]
dotnet_diagnostic.<rule-ID>.severity = none
```

規則の重大度の詳細については、「 [規則の重要度の構成](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level)」を参照してください。

## <a name="use-a-preprocessor-directive"></a>プリプロセッサディレクティブを使用する

[#Pragma warning (C#)](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)または[Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md)ディレクティブを使用して、特定のコード行についてのみ警告を非表示にします。

```csharp
    try { ... }
    catch (Exception e)
    {
#pragma warning disable CA2200 // Rethrow to preserve stack details
        throw e;
#pragma warning restore CA2200 // Rethrow to preserve stack details
    }
```

```vb
    Try
        ...
    Catch e As Exception
#Disable Warning CA2200 ' Rethrow to preserve stack details
        Throw e
#Enable Warning CA2200 ' Rethrow to preserve stack details
    End Try
```

## <a name="use-the-suppressmessageattribute"></a>SuppressMessageAttribute を使用する

を使用すると、 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> ソースファイルまたはプロジェクトのグローバル抑制ファイル (*GlobalSuppressions.cs* または *globalsuppressions*) のいずれかで警告を非表示にすることができます。 この属性は、プロジェクトまたはファイルの特定の部分のみで警告を非表示にする方法を提供します。

属性の2つの必須の位置指定パラメーター <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> は、ルールの *カテゴリ* と *ルール ID* です。 次のコードスニペットは `"Usage"` 、 `"CA2200:Rethrow to preserve stack details"` これらのパラメーターにとを渡します。

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.")]
private static void IngorableCharacters()
{
    try
    {
        ...
    }
    catch (Exception e)
    {
        throw e;
    }
}
```

グローバル抑制ファイルに属性を追加する場合は、抑制の範囲を目的のレベルに [限定](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) します。たとえば、のようにし `"member"` ます。 警告を抑制する API は、プロパティを使用して指定し <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> ます。

```csharp
[assembly: SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.", Scope = "member", Target = "~M:MyApp.Program.IngorableCharacters")]
```

明示的に指定されたユーザーソースにマップされない、コンパイラによって生成されるコードの警告を抑制するには、抑制属性をグローバル抑制ファイルに配置する必要があります。 たとえば、次のコードは、コンパイラによって生成されたコンストラクターに対する違反を抑制します。

```csharp
[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="MyTools.Type..ctor()")]
```

## <a name="see-also"></a>関連項目

- [違反を抑制する (Visual Studio)](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)
