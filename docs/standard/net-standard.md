---
title: .NET Standard
description: .NET Standard、そのバージョン、それをサポートする .NET 実装について学習します。
ms.date: 10/05/2020
ms.prod: dotnet
ms.technology: dotnet-standard
ms.custom: updateeachrelease
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: 93fb10538441d939e95bb48dcdd0e61d9267dde0
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/24/2020
ms.locfileid: "97765034"
---
# <a name="net-standard"></a>.NET Standard

[.NET Standard](https://github.com/dotnet/standard) は、複数の .NET 実装で使用できる .NET API の正式な仕様です。 .NET Standard の背後にある意図は、.NET エコシステムの高度な統一性を確立することでした。 しかし、.NET 5 には統一性を確立するための別のアプローチが採用されており、この新しいアプローチによって、多くのシナリオで .NET Standard が不要になります。 詳細については、後の「[.NET 5 と .NET Standard](#net-5-and-net-standard)」を参照してください。

## <a name="net-implementation-support"></a>.NET 実装のサポート

さまざまな .NET 実装が、.NET Standard の特定のバージョンを対象とします。 各 .NET 実装バージョンは、それがサポートしている最高の .NET Standard バージョンをアドバタイズし、そのことは以前のバージョンもサポートしていることを意味します。 たとえば、.NET Framework 4.6 は .NET Standard 1.3 を実装しており、このことは、.NET Standard のバージョン 1.0 ～ 1.3 で定義されているすべての API を公開していることを意味します。 同様に、.NET Framework 4.6.1 には .NET Standard 1.4 が実装されていますが、.NET 5.0 には .NET Standard 2.1 が実装されています。

次の表は、.NET Standard の各バージョンがサポートされている **最小** の実装バージョンの一覧です。 つまり、一覧に示されている実装以降のバージョンでも、対応する .NET Standard バージョンがサポートされています。 たとえば、.NET Core 2.1 以降のバージョンによって .NET Standard 2.0 以前のバージョンがサポートされています。

[!INCLUDE [net-standard-table](../../includes/net-standard-table.md)]

対象にすることができる最高バージョンの .NET Standard を確認するには、次の手順を実行します。

1. 実行する .NET 実装を示す行を探します。
1. この行内で、右から左の方向に、バージョンを示す列を探します。
1. 列ヘッダーには、ターゲットでサポートされている .NET Standard バージョンが示されます。 任意の古い .NET Standard バージョンをターゲットにすることもできます。 .NET Standard の今後のバージョンでも実装はサポートされます。
1. 対象にするプラットフォームごとに、この手順を繰り返します。 複数のターゲット プラットフォームがある場合は、その中から低いバージョンを選択することをお勧めします。 たとえば、.NET Framework 4.8 と .NET 5.0 で実行する場合、使用できる .NET Standard の最高のバージョンは .NET Standard 2.0 です。

### <a name="which-net-standard-version-to-target"></a>対象にする .NET Standard バージョン

.NET Standard バージョンをターゲットに選択する場合、次のトレードオフを考慮する必要があります。

- バージョンが高くなるほど、ユーザーのライブラリのコードで使用できる API は多くなります。
- バージョンが低くなるほど、ユーザーのライブラリを使用できるアプリやライブラリが増えます。

可能な限り "*最小*" のバージョンの .NET Standard をターゲットにすることをお勧めします。 そのため、対象にする最高バージョンの .NET Standard を見つけたら、次の手順を実行します。

1. 1 つ低いバージョンの .NET Standard を対象にしてプロジェクトをビルドします。
2. プロジェクトのビルドが成功したら、手順 1 を繰り返します。 失敗した場合は、対象を次に高いバージョンに変更します。これが対象のバージョンです。

ただし、下位バージョンの .NET Standard を対象にしている場合、さまざまな依存関係のサポートが導入されます。 お使いのプロジェクトが .NET Standard 1.x を対象としている場合、.NET Standard 2.0 "*も*" 対象にすることをお勧めします。 これにより、.NET Standard 2.0 と互換性のある実装上で実行されるライブラリのユーザーに対しては、依存関係グラフが簡略化され、ダウンロードの必要なパッケージの数が減ります。

### <a name="net-standard-versioning-rules"></a>.NET Standard のバージョン管理規則

バージョン管理規則は主に 2 つあります。

- 追加式: .NET Standard バージョンは論理的に同心円形です。高位のバージョンには、旧バージョンのすべての API が組み込まれています。 バージョン間に互換性に影響する変更はありません。
- 不変:出荷後、.NET Standard のバージョンは固定されます。

2\.1 より後に .NET Standard の新しいバージョンはありません。 詳細については、後の「[.NET 5 と .NET Standard](#net-5-and-net-standard)」を参照してください。

## <a name="specification"></a>仕様

.NET Standard の仕様は、標準化された API のセットです。 この仕様は、.NET 実装、具体的には Microsoft (.NET Framework、.NET Core、Mono を含む) と Unity によって管理されています。

### <a name="official-artifacts"></a>正式な成果物

正式な仕様は、標準に含まれる API を定義する一連の *.cs* ファイルです。 [dotnet/standard リポジトリ](https://github.com/dotnet/standard)の [ref](https://github.com/dotnet/standard/tree/master/src/netstandard/ref) ディレクトリに.NET Standard API が定義されています。

[NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) メタパッケージ ([ソース](https://github.com/dotnet/standard/blob/master/src/netstandard/pkg/NETStandard.Library.dependencies.props)) は、1 つ以上の .NET Standard のバージョンを定義する (一部) ライブラリのセットについて説明しています。

`System.Runtime` などの特定のコンポーネントは、次のように説明されています。

- .NET Standard の一部 (そのスコープだけ)。
- そのスコープの .NET Standard の複数のバージョン。

便利に読めるようにし、特定の開発者シナリオ (コンパイラを使用するなど) を可能にするために、派生成果物が提供されています。

- [マークダウン形式の API 一覧](https://github.com/dotnet/standard/tree/master/docs/versions)
- NuGet パッケージとして配布され、[NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/) メタパッケージによって参照される参照アセンブリ。

### <a name="package-representation"></a>パッケージ表現

.NET Standard 参照アセンブリの主要な配布手段は NuGet パッケージです。 実装は、各 .NET 実装に適切なさまざまな方法で配布されます。

NuGet パッケージは 1 つまたは複数の[フレームワーク](frameworks.md)を対象にしています。 .NET Standard パッケージは、".NET Standard" フレームワークを対象にしています。 `netstandard` [コンパクト TFM](frameworks.md) (`netstandard1.4` など) を使用して、.NET Standard フレームワークを対象にすることができます。 .NET の複数の実装で実行することが意図されたライブラリは、このフレームワークをターゲットにする必要があります。 広範なセットの API の場合、.NET Standard 1.6 から 2.0 の間に使用できる API の数は 2 倍以上になったため、`netstandard2.0` を対象としてください。

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library/) メタパッケージは .NET Standard を定義する NuGet パッケージの完全なセットを参照しています。  `netstandard` を対象とする最も一般的な方法は、このメタパッケージを参照することです。 それは、.NET Standard を定義する約 40 の .NET ライブラリと関連する API について説明しており、それらにアクセスできるようにしています。 `netstandard` を対象とする追加のパッケージを参照して、追加の API にアクセスできます。

### <a name="versioning"></a>バージョン管理

仕様は 1 つだけではありませんが、直線的にバージョン管理された API のセットです。 標準の最初のバージョンは、API のベースライン セットを構築しています。 それ以降のバージョンでは、API が追加され、以前のバージョンによって定義された API を継承しています。 標準から API を削除するために確立された取り決めはありません。

.NET Standard は、1 つの .NET 実装に固有ではなく、それらの実装のいずれかのバージョン管理スキームに一致することもありません。

既に説明したように、2.1 より後に .NET Standard の新しいバージョンはありません。

## <a name="target-net-standard"></a>ターゲットの .NET Standard

`netstandard` フレームワークと `NETStandard.Library` メタパッケージの組み合わせを使用して、[.NET Standard Library をビルド](../core/tutorials/libraries.md)できます。

## <a name="net-framework-compatibility-mode"></a>.NET Framework 互換モード

.NET Standard 2.0 以降、.NET Framework 互換モードが導入されました。 この互換モードにより、.NET Standard プロジェクトは、あたかも .NET Standard にコンパイルされたかのように .NET Framework ライブラリを参照できます。 .NET Framework ライブラリの参照は、Windows Presentation Foundation (WPF) API を使用するライブラリのような、一部のプロジェクトでは機能しません。

詳細については、「[.NET Framework 互換モード](../core/porting/third-party-deps.md#net-framework-compatibility-mode)」を参照してください。

## <a name="net-standard-libraries-and-visual-studio"></a>.NET Standard ライブラリと Visual Studio

Visual Studio で .NET Standard ライブラリを作成するには、Windows の場合 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) または Visual Studio 2017 バージョン 15.3 以降、macOS の場合 [Visual Studio for Mac バージョン 7.1](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 以降がインストールされている必要があります。

プロジェクトで .NET Standard 2.0 ライブラリを使用するだけである場合は、Visual Studio 2015 でこれを行うこともできます。 ただし、NuGet クライアント 3.6 以降がインストールされている必要があります。 Visual Studio 2015 用の NuGet クライアントは、[NuGet のダウンロード](https://www.nuget.org/downloads)のページからダウンロードできます。

## <a name="net-5-and-net-standard"></a>.NET 5 と .NET Standard

.NET 5 は、Microsoft が積極的に開発している .NET の実装です。 Windows デスクトップ アプリとクロスプラットフォーム コンソール アプリ、クラウド サービス、Web サイトに使用できる統一された機能と API のセットを備えた単一の製品です。 .NET 5.0 [TFM](frameworks.md) には、次のような幅広いシナリオが反映されています。

* `net5.0`

  この TFM は、どこでも実行できるコードを対象としています。 いくつか例外はありますが、クロスプラットフォームで動作するテクノロジだけが含まれています。 .NET 5 コードの場合、`net5.0` によって `netcoreapp` と `netstandard` 両方の TFM が置き換えられます。

* `net5.0-windows`

  これは、`net5.0` によって参照されているすべてのものに OS 固有の機能を追加する [OS 固有の TFM](frameworks.md#net-5-os-specific-tfms) の例です。

### <a name="when-to-target-net50-vs-netstandard"></a>net5.0 と netstandard をターゲットにするタイミング

`netstandard` がターゲットの既存のコードの場合は、TFM を `net5.0` に変更する必要はありません。 .NET 5.0 により、.NET Standard 2.1 以前が実装されています。 .NET Standard から .NET 5.0 にターゲットを変更する唯一の理由は、より多くのランタイム機能、言語機能、または API にアクセスできるようにすることです。 たとえば、C# 9 を使用するには、.NET 5.0 をターゲットにする必要があります。 .NET 5.0 と .NET Standard をマルチターゲットにして、新しい機能にアクセスしながら、他の .NET 実装でライブラリを使用できるようにすることができます。

.NET 5 用の新しいコードのガイドラインを次に示します。

* アプリのコンポーネント

  アプリケーションを複数のコンポーネントに分割するためにライブラリを使用している場合は、`net5.x` をターゲットにすることをお勧めします。`5.x` は、アプリケーションでターゲットにできる最も古い .NET 5 バージョンです。 わかりやすくするために、アプリケーションを構成するすべてのプロジェクトを、同じバージョンの .NET にするのが最善の方法です。 このようにすると、同じ BCL 機能をどこでも使用できます。

* 再利用可能なライブラリ

  NuGet で配布する予定の再利用可能なライブラリを構築している場合は、リーチと使用可能な機能セットの間のトレードオフを検討してください。 .NET Standard 2.0 は .NET Framework によってサポートされている最新バージョンであるため、非常に大きな機能セットで良好なリーチが提供されます。 リーチの増加が最小限で、使用可能な機能セットが制限されるため、.NET Standard 1.x をターゲットにすることはお勧めしません。

  .NET Framework をサポートする必要がない場合は、.NET Standard 2.1 または .NET 5 を使用することもできます。 .NET Standard 2.1 は使わずに、.NET 5 に直接進むことをお勧めします。 最も広く使用されているライブラリは、最終的に .NET Standard 2.0 と .NET 5 の両方のマルチターゲットになります。 .NET Standard 2.0 をサポートすると、最大のリーチになります。一方、.NET 5 をサポートすると、.NET 5 を既に使用している顧客に対して最新のプラットフォーム機能を利用できるようになります。

### <a name="net-standard-problems"></a>.NET Standard の問題

ここで .NET Standard にあるいくつかの問題を示しておくと、.NET 5 がプラットフォームとワークロード間でコードを共有するための優れた方法である理由を説明するのに役立ちます。

- 新しい API が追加されるのが遅い

  .NET Standard は、すべての .NET 実装でサポートする必要がある API セットとして作成されているため、新しい API を追加する提案に対してレビュー プロセスがありました。 目標は、現在および将来のすべての .NET プラットフォームで実装できる API のみを標準化することでした。 その結果、ある機能が特定のリリースにない場合、Standard のバージョンに追加されるまで数年待たなければならないことがありました。 新しいバージョンの .NET Standard が広くサポートされるようになるまでは、さらに長く待ちました。

  **.NET 5 での解決策:** コード ベースが共有されているため、機能が実装されるときには、.NET 5 のすべてのアプリとライブラリで既に使用できるようになっています。 また、API の仕様とその実装に違いがないため、.NET Standard の場合よりはるかに早く、新機能を利用できるようになります。

- 複雑なバージョン管理

  API の仕様とその実装が分かれているため、API の仕様のバージョンと実装のバージョンの間のマッピングが複雑になります。 このような複雑さは、この記事で前に示した表と、その解釈方法の説明を見れば明らかです。

  **.NET 5 での解決策:** .NET 5.x の場合は、API の仕様とその実装は分かれていません。 その結果、TFM のスキームが簡単になります。 TFM のプレフィックスは、すべてのワークロードに対して 1 つです。`net5.0` が、ライブラリ、コンソール アプリ、Web アプリに使用されます。 唯一のバリエーションは、特定のプラットフォームに対する[プラットフォーム固有の API を指定するサフィックス](frameworks.md#net-5-os-specific-tfms)です (`net5.0-windows` など)。 このような TFM の名前付け規則のおかげで、特定のアプリで特定のライブラリを使用できるかどうかを簡単に判断できます。 .NET Standard のようなバージョン番号対応テーブルは必要ありません。

- 実行時のプラットフォーム非サポート例外

  .NET Standard の場合、プラットフォーム固有の API が公開されます。 移植できない場合であっても、コードはエラーなしでコンパイルされ、任意のプラットフォームに移植できるように見えます。 特定の API の実装がないプラットフォームで実行すると、実行時エラーが発生します。

  **.NET 5 での解決策:** .NET 5 SDK には、既定で有効になるコード アナライザーが含まれています。 実行しようとしているプラットフォームでサポートされていない API をうっかり使用すると、プラットフォーム互換性アナライザーによって検出されます。 詳細については、「[プラットフォーム互換性アナライザー](analyzers/platform-compat-analyzer.md)」を参照してください。

### <a name="net-standard-not-deprecated"></a>.NET Standard は非推奨ではない

.NET Standard は、複数の .NET 実装で使用できるライブラリにまだ必要です。 次のシナリオの場合、.NET Standard をターゲットにすることをお勧めします。

* `netstandard2.0` を使用して、.NET Framework と .NET の他のすべての実装の間でコードを共有する。
* `netstandard2.1` を使用して、Mono、Xamarin、.NET Core 3.x の間でコードを共有する。

## <a name="see-also"></a>関連項目

- [.NET Standard のバージョン (ソース)](https://github.com/dotnet/standard/blob/master/docs/versions.md)
- [.NET Standard のバージョン (対話型 UI)](https://dotnet.microsoft.com/platform/dotnet-standard#versions)
- [.NET Standard ライブラリを構築する](../core/tutorials/library-with-visual-studio.md)
- [クロス プラットフォーム ターゲット](./library-guidance/cross-platform-targeting.md)
