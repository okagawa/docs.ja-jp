---
title: MSBuild によるマニフェスト ファイル名の生成方法
description: MSBuild によってコンパイル時に生成されるリソース マニフェスト ファイル名の名前に影響する要因について説明します。
ms.date: 05/08/2020
ms.topic: conceptual
ms.openlocfilehash: 2e0461e34bbd7f8da35bea1db1913a32915c7117
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970682"
---
# <a name="how-resource-manifest-files-are-named"></a>リソース マニフェスト ファイルの名前付け方法

MSBuild により .NET Core プロジェクトがコンパイルされると、 *.resx* ファイル拡張子を持つ XML リソース ファイルがバイナリ *.resources* ファイルに変換されます。 バイナリ ファイルは、コンパイラの出力に埋め込まれ、<xref:System.Resources.ResourceManager> で読み取ることができます。 この記事では、MSBuild によって各 *.resources* ファイルの名前がどのように選択されるかについて説明します。

> [!TIP]
> リソース項目をプロジェクト ファイルに明示的に追加するときに、それが [.NET Core の既定の include glob にも含まれる](../project-sdk/overview.md#default-includes-and-excludes)場合、ビルド エラーが発生します。 リソース ファイルを `EmbeddedResource` 項目として手動で含めるには、`EnableDefaultEmbeddedResourceItems` プロパティを false に設定します。

## <a name="default-name"></a>既定名

.NET Core 3.0 以降では、次の両方の条件が満たされる場合に、リソース マニフェストの既定名が使用されます。

- リソース ファイルが、`LogicalName`、`ManifestResourceName`、または `DependentUpon` メタデータを持つ `EmbeddedResource` 項目としてプロジェクト ファイルに明示的に含まれていない。
- `EmbeddedResourceUseDependentUponConvention` プロパティがプロジェクト ファイルで `false` に設定されていない。 既定では、このプロパティは `true`に設定されています。 詳細については、「[EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention)」を参照してください。

リソース ファイルが、同じルート ファイル名のソース ファイル ( *.cs* または *.vb*) と併置されている場合、ソース ファイルで定義されている最初の型の完全な名前がマニフェスト ファイル名に使用されます。 たとえば、`MyNamespace.Form1` が *Form1.cs* で定義されている最初の型であり、*Form1.cs* が *Form1.resx* と併置されている場合、そのリソース ファイルに対して生成されたマニフェスト名は *MyNamespace.Form1.resources* となります。

## <a name="logicalname-metadata"></a>LogicalName メタデータ

リソース ファイルが `LogicalName` メタデータを持つ `EmbeddedResource` 項目としてプロジェクト ファイルに明示的に含まれている場合、`LogicalName` 値がマニフェスト名として使用されます。 `LogicalName` は、他のメタデータや設定よりも優先されます。

たとえば、次のプロジェクト ファイル スニペットで定義されているリソース ファイルのマニフェスト名は、*SomeName.resources* となります。

```xml
<EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
```

- または -

```xml
<EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
```

## <a name="manifestresourcename-metadata"></a>ManifestResourceName メタデータ

リソース ファイルが `ManifestResourceName` メタデータを持つ (`LogicalName` は存在しない)`EmbeddedResource` 項目としてプロジェクト ファイルに明示的に含まれている場合、`ManifestResourceName` 値は、ファイル拡張子 *.resources* と組み合わされ、マニフェスト ファイル名として使用されます。

たとえば、次のプロジェクト ファイル スニペットで定義されているリソース ファイルのマニフェスト名は、*SomeName.resources* となります。

```xml
<EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
```

次のプロジェクト ファイル スニペットで定義されているリソース ファイルのマニフェスト名は、*SomeName.fr-FR.resources* となります。

```xml
<EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
```

## <a name="dependentupon-metadata"></a>DependentUpon メタデータ

リソース ファイルが `DependentUpon` メタデータを持つ (`LogicalName` と `ManifestResourceName` は存在しない) `EmbeddedResource` 項目としてプロジェクト ファイルに明示的に含まれている場合、`DependentUpon` で定義されているソース ファイルからの情報がリソース マニフェストのファイル名に使用されます。 具体的には、ソース ファイルで定義されている最初の型の名前がマニフェスト名で次のように使用されます: *Namespace.Classname\[.Culture].resources*。

たとえば、次のプロジェクト ファイル スニペットで定義されているリソース ファイルのマニフェスト名は、*Namespace.Classname.resources* となります (ここで、`Namespace.Classname` は *MyTypes.cs* で定義されている最初のクラスです)。

```xml
<EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
```

次のプロジェクト ファイル スニペットで定義されているリソース ファイルのマニフェスト名は *Namespace.Classname.fr-FR.resources* となります (ここで、`Namespace.Classname` は *MyTypes.cs* で定義されている最初のクラスです)。

```xml
<EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
```

## <a name="embeddedresourceusedependentuponconvention-property"></a>EmbeddedResourceUseDependentUponConvention プロパティ

プロジェクト ファイルで `EmbeddedResourceUseDependentUponConvention` が `false` に設定されている場合、各リソース マニフェストのファイル名は、プロジェクトのルート名前空間と、プロジェクト ルートから *.resx* ファイルへの相対パスに基づきます。 さらに具体的に言うと、生成されるリソース マニフェストのファイル名は *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources* となります。 これは、3.0 より前の .NET Core バージョンでマニフェスト名を生成するために使用されるロジックでもあります。

> [!NOTE]
>
> - `RootNamespace` が定義されていない場合は、既定でそのプロジェクト名になります。
> - `LogicalName`、`ManifestResourceName`、または `DependentUpon` メタデータがプロジェクト ファイルで `EmbeddedResource` 項目に対して指定されている場合、この名前付けルールはそのリソース ファイルには適用されません。

## <a name="see-also"></a>関連項目

- [マニフェスト リソースの名前付けのしくみ](https://gist.github.com/BenVillalobos/041673b9a73bec60fdc3bf0f86fae62a)
- [.NET Core SDK プロジェクトの MSBuild プロパティ](../project-sdk/msbuild-props.md)
- [MSBuild に関する破壊的変更](../compatibility/msbuild.md)
