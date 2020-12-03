---
title: '破壊的変更: WPF アプリと WinForms アプリで OutputType が WinExe に設定されている'
description: .NET 5.0 での破壊的変更について学習します。Windows フォーム アプリで OutputType が自動的に WinExe に設定されます。
ms.date: 09/18/2020
ms.openlocfilehash: 072c5b11c8304eb540e176ce9747930789f28505
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760022"
---
# <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a>WPF アプリと WinForms アプリで OutputType が WinExe に設定されている

`OutputType` は、Windows Presentation Foundation (WPF) アプリと Windows フォーム アプリでは、自動的に `WinExe` に設定されます。 `OutputType` が `WinExe` に設定されている場合、アプリの実行時にコンソール ウィンドウは開きません。

## <a name="change-description"></a>変更内容

以前のバージョンの .NET では、プロジェクト ファイルで `OutputType` に指定されている値が使用されます。 次に例を示します。

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

.NET 5.0 以降では、WPF アプリと Windows フォーム アプリで `OutputType` が `WinExe` に自動的に設定されます。 次に例を示します。

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

## <a name="reason-for-change"></a>変更理由

WPF アプリまたは Windows フォーム アプリの実行時に、ほとんどのユーザーがコンソール ウィンドウを開かないことを前提としています。 さらに、[これらの種類のアプリケーションでは .NET SDK が使用され](sdk-and-target-framework-change.md) (Windows Desktop SDK が使用されるのではなく)、正しい既定値が設定されるようになります。 さらに、iOS と Android を対象としたサポートが追加されると、これらすべてで同じ出力の種類が使用される場合に、複数のプラットフォーム間で複数のターゲットを指定することが容易になります。

## <a name="version-introduced"></a>導入されたバージョン

.NET 5.0

## <a name="recommended-action"></a>推奨アクション

ユーザー側の対応は必要ありません。 ただし、以前の動作に戻す場合は、プロジェクト ファイルの `DisableWinExeOutputInference` プロパティを `true` に設定します。

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

## <a name="affected-apis"></a>影響を受ける API

API 分析では検出できません。

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
