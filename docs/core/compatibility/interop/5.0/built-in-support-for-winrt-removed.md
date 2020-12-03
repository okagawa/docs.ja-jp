---
title: '破壊的変更: WinRT の組み込みサポートは .NET から削除されています'
description: .NET 5.0 での相互運用に関する破壊的変更について学習します。この変更により、WinRT の組み込みサポートは .NET から削除されています。
ms.date: 10/13/2020
ms.openlocfilehash: 61d8e26d06c232a7bfa1891a2159f5232f747b8a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759824"
---
# <a name="built-in-support-for-winrt-is-removed-from-net"></a>WinRT の組み込みサポートは .NET から削除されています

.NET の [Windows runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) API を使用するための組み込みサポートは削除されています。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="change-description"></a>変更の説明

以前は、CoreCLR では、[Windows メタデータ (WinMD) ファイル](/uwp/winrt-cref/winmd-files)を使用し、WinRT タイプをアクティブ化し、使用していました。 .NET 5.0 以降、CoreCLR では、WinMD ファイルを直接使用することができなくなりました。

サポートされていないアセンブリを参照しようとすると、<xref:System.IO.FileNotFoundException> が表示されます。 WinRT クラスをアクティブ化すると、<xref:System.PlatformNotSupportedException> が表示されます。

この破壊的変更は次の理由から行われました。

- WinRT は .NET ランタイムとは別に開発し、改善できるため。
- iOS や Android など、他のオペレーティング システムに提供されている相互運用システムと釣り合いを取るため。
- C# の機能、中間言語 (IL) のリンク、Ahead Of Time (AOT) コンパイルなど、その他の .NET 機能を活用するため。
- .NET ランタイム コードベースを簡略化するため。

## <a name="recommended-action"></a>推奨アクション

- [Microsoft.Windows.SDK.Contracts パッケージ](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts)の参照を削除します。  代わりに、プロジェクトの `TargetFramework` プロパティ経由でアクセスする Windows API のバージョンを指定します。  次に例を示します。

  ```xml
  <TargetFramework>net5.0-windows10.0.19041</TargetFramework>
  ```

- [C#/WinRT](/windows/uwp/csharp-winrt/) ツール チェーンを使用し、.NET 5.0 以降のバージョンで WinRT の API と型を生成するか、カスタマイズします。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

### Category

Interop

-->
