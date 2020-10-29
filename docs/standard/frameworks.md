---
title: SDK スタイル プロジェクトでのターゲット フレームワーク - .NET
description: .NET アプリとライブラリのターゲット フレームワークについて説明します。
ms.date: 09/08/2020
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: 85bc05f07cfcc5f59a8a27790ee3d78a497cecdc
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223468"
---
# <a name="target-frameworks-in-sdk-style-projects"></a>SDK スタイルのプロジェクトでのターゲット フレームワーク

アプリまたはライブラリでフレームワークをターゲットに設定するときは、アプリまたはライブラリで使用できるようにする API のセットを指定します。 プロジェクト ファイルでターゲット フレームワークを指定するには、ターゲット フレームワーク モニカー (TFM) を使用します。

アプリまたはライブラリでは、[.NET Standard](net-standard.md) のバージョンをターゲットにできます。 .NET Standard のバージョンは、.NET のすべての実装で標準化された API のセットを表します。 たとえば、ライブラリは、.NET Standard 1.6 をターゲットにして、.NET Core と .NET Framework で機能する API に同じコードベースを使ってアクセスできます。

また、アプリまたはライブラリは、.NET の特定の実装をターゲットにして、実装固有の API にアクセスすることもできます。 たとえば、Xamarin.iOS (`Xamarin.iOS10` など) をターゲットにするアプリからは Xamarin が提供する iOS 10 用の iOS API ラッパーにアクセスでき、ユニバーサル Windows プラットフォーム (UWP、`uap10.0`) をターゲットにするアプリからは Windows 10 を実行するデバイス用にコンパイルできる API にアクセスできます。

一部のターゲット フレームワーク (.NET Framework など) では、API はフレームワークがシステムにインストールするアセンブリによって定義され、アプリケーション フレームワーク API (ASP.NET など) を含む場合があります。

パッケージ ベースのターゲット フレームワーク (.NET Standard、.NET Core など) では、API はアプリまたはライブラリに含まれるパッケージによって定義されます。 " *メタパッケージ* " は、それ独自の内容はなく、依存するもの (他のパッケージ) のリストを保持している NuGet パッケージです。 NuGet パッケージ ベースのターゲット フレームワークでは、全体としてフレームワークを構成するすべてのパッケージを参照するメタパッケージが暗黙的に指定されます。

## <a name="latest-versions"></a>最新バージョン

次の表では、最も一般的なターゲット フレームワーク、それらの参照方法、およびそれらが実装する [.NET Standard](net-standard.md) のバージョンを定義します。 これらのターゲット フレームワークのバージョンは、最新の安定したバージョンです。 プレリリース バージョンは記載されていません。 ターゲット フレームワーク モニカー (TFM) は、.NET アプリまたはライブラリのターゲット フレームワークを指定するための標準化されたトークン形式です。

| ターゲット フレーム      | 最新 <br/> 安定バージョン | ターゲット フレームワーク モニカー (TFM) | 実装済み <br/> .NET Standard バージョン |
| :-: | :-: | :-: | :-: |
| .NET Standard         | 2.1                         | netstandard2.1                 | 該当なし                                     |
| .NET Core             | 3.1                         | netcoreapp3.1                  | 2.1                                     |
| .NET Framework        | 4.8                         | net48                          | 2.0                                     |

## <a name="supported-target-frameworks"></a>サポート対象のターゲット フレームワーク

ターゲット フレームワークは、通常、TFM によって参照されます。 次の表に、.NET SDK および NuGet クライアントによってサポートされるターゲット フレームワークを示します。 同等のものがかっこ内に示されています。 たとえば、`win81` は `netcore451` と同等の TFM です。

| [対象とする Framework]           | TFM |
| -------------------------- | --- |
| .NET 5 (および .NET Core)     | netcoreapp1.0<br>netcoreapp1.1<br>netcoreapp2.0<br>netcoreapp2.1<br>netcoreapp2.2<br>netcoreapp3.0<br>netcoreapp3.1<br>net5.0* |
| .NET Standard              | netstandard1.0<br>netstandard1.1<br>netstandard1.2<br>netstandard1.3<br>netstandard1.4<br>netstandard1.5<br>netstandard1.6<br>netstandard2.0<br>netstandard2.1 |
| .NET Framework             | net11<br>net20<br>net35<br>net40<br>net403<br>net45<br>net451<br>net452<br>net46<br>net461<br>net462<br>net47<br>net471<br>net472<br>net48 |
| Windows ストア              | netcore [netcore45]<br>netcore45 [win] [win8]<br>netcore451 [win81] |
| .NET Micro Framework       | netmf |
| Silverlight                | sl4<br>sl5 |
| Windows Phone              | wp [wp7]<br>wp7<br>wp75<br>wp8<br>wp81<br>wpa81 |
| ユニバーサル Windows プラットフォーム | uap [uap10.0]<br>uap10.0 [win10] [netcore50] |

\* .NET 5.0 以降の TFM には OS 固有のバリエーションが含まれています。 詳細については、次のセクション「[.NET 5 OS 固有の TFM](#net-5-os-specific-tfms)」を参照してください。

### <a name="net-5-os-specific-tfms"></a>.NET 5 OS 固有の TFM

たとえば `net5.0` などの .NET 5.0 以降の各 TFM には、OS 固有のバインドを含む TFM のバリエーションがあります。 これらのバリエーションを次の表に示します。

| OS 固有の形式 | 例        |
|--------------------|----------------|
| \<base-tfm>-android | net5.0-android |
| \<base-tfm>-ios     | net5.0-ios     |
| \<base-tfm>-macos   | net5.0-macos   |
| \<base-tfm>-tvos    | net5.0-tvos    |
| \<base-tfm>-watchos | net5.0-watchos |
| \<base-tfm>-windows | net5.0-windows |

たとえば `net5.0-ios12.0` のように、OS のバージョンを任意で指定することもできます。

.NET 5 TFM の詳細については、「[Target framework names in .NET 5](https://github.com/dotnet/designs/blob/master/accepted/2020/net5/net5.md)」(.NET 5 でのターゲット フレームワーク名) を参照してください。

## <a name="how-to-specify-a-target-framework"></a>ターゲット フレームワークを指定する方法

ターゲット フレームワークはプロジェクト ファイルで指定します。 単一のターゲット フレームワークを指定するときは、 **TargetFramework** 要素を使います。 次のコンソール アプリのプロジェクト ファイルでは、.NET 5.0 をターゲットにする方法が示されています。

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
```

複数のターゲット フレームワークを指定するときは、各ターゲット フレームワークに対するアセンブリを条件付きで参照できます。 コードでは、プリプロセッサ シンボルと *if-then-else* ロジックを使うことで、これらのアセンブリに対して条件付きでコンパイルできます。

次のライブラリ プロジェクトでは、.NET Standard (`netstandard1.4`) と .NET Framework (`net40` および `net45`) の API がターゲットにされています。 ターゲット フレームワークが複数あるときは、複数形の **TargetFrameworks** 要素を使います。 ライブラリが 2 つの .NET Framework TFM に対してコンパイルされる場合、`Condition` 属性には実装固有のパッケージが含まれます。

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Conditionally obtain references for the .NET Framework 4.0 target -->
  <ItemGroup Condition=" '$(TargetFramework)' == 'net40' ">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Conditionally obtain references for the .NET Framework 4.5 target -->
  <ItemGroup Condition=" '$(TargetFramework)' == 'net45' ">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>

</Project>
```

ライブラリまたはアプリ内で、[プリプロセッサ ディレクティブ](../csharp/language-reference/preprocessor-directives/preprocessor-if.md)を使用して各ターゲット フレームワーク用にコンパイルするための条件付きコードを記述します。

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

SDK スタイル プロジェクトを使用する場合、ビルド システムは、「[サポートされるターゲット フレームワークのバージョン](#supported-target-frameworks)」の表で示されているターゲット フレームワークを表すプリプロセッサ シンボルを認識します。 .NET Standard、.NET Core、または NET 5 の TFM を表すシンボルを使うときは、ドットとハイフンをアンダースコアに置き換え、小文字を大文字に変更します (たとえば、`netstandard1.4` のシンボルは `NETSTANDARD1_4` です)。

.NET ターゲット フレームワークのプリプロセッサ シンボルの完全な一覧を次に示します。

[!INCLUDE [Preprocessor symbols](../../includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a>非推奨のターゲット フレームワーク

次のターゲット フレームワークは非推奨とされます。 これらのターゲット フレームワークをターゲットにするパッケージは、指定されている代替のものに移行する必要があります。

| 非推奨の TFM                                                                             | Replacement |
| ------------------------------------------------------------------------------------------ | ----------- |
| aspnet50<br>aspnetcore50<br>dnxcore50<br>dnx<br>dnx45<br>dnx451<br>dnx452                  | netcoreapp  |
| dotnet<br>dotnet50<br>dotnet51<br>dotnet52<br>dotnet53<br>dotnet54<br>dotnet55<br>dotnet56 | netstandard |
| netcore50                                                                                  | uap10.0     |
| win                                                                                        | netcore45   |
| win8                                                                                       | netcore45   |
| win81                                                                                      | netcore451  |
| win10                                                                                      | uap10.0     |
| winrt                                                                                      | netcore45   |

## <a name="see-also"></a>参照

- [クロス プラットフォーム ツールによるライブラリの開発](../core/tutorials/libraries.md)
- [.NET Standard](net-standard.md)
- [.NET Core バージョン管理](../core/versions/index.md)
- [dotnet/standard GitHub リポジトリ](https://github.com/dotnet/standard)
- [NuGet Tools GitHub リポジトリ](https://github.com/joelverhagen/NuGetTools)
- [.NET のフレームワーク プロファイル](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)
