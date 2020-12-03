---
title: 破壊的変更:OSPlatform 属性の名前変更または削除
description: Core .NET ライブラリにおける .NET 5.0 の破壊的変更について学習します。プレビュー バージョンで実装された OS プラットフォームの属性が削除または名前変更されました。
ms.date: 11/01/2020
ms.openlocfilehash: 7e709b84005a7b807e390e12d9f36d8b4f73a9df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759416"
---
# <a name="osplatform-attributes-renamed-or-removed"></a>OSPlatform 属性の名前変更または削除

.NET 5.0 Preview 8 で実装された、`MinimumOSPlatformAttribute`、`RemovedInOSPlatformAttribute`、および `ObsoletedInOSPlatformAttribute` 属性が、削除または名前変更されました。

## <a name="change-description"></a>変更内容

.NET 5.0 Preview 8 で <xref:System.Runtime.Versioning> 名前空間に次の属性が実装されました。

- `MinimumOSPlatformAttribute`
- `RemovedInOSPlatformAttribute`
- `ObsoletedInOSPlatformAttribute`

.NET 5.0 Preview 8 のプロジェクトで、`net5.0-windows` などの[ターゲット フレームワーク モニカー](../../../../standard/frameworks.md)を使用し、.NET 5 の OS 固有のフレーバーをターゲットとしている場合、ビルドでは、アセンブリレベルの `System.Runtime.Versioning.MinimumOSPlatformAttribute` 属性が追加されます。

.NET 5.0 RC1 では、`ObsoletedInOSPlatformAttribute` が削除され、`MinimumOSPlatformAttribute` と `RemovedInOSPlatformAttribute` が次のように名前変更されています。

| Preview 8 での名前 | RC1 以降での名前 |
| - | - |
| `MinimumOSPlatformAttribute` | <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> |
| `RemovedInOSPlatformAttribute` | <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> |

.NET 5.0 RC1 以降のプロジェクトで、`net5.0-windows` などの[ターゲット フレームワーク モニカー](../../../../standard/frameworks.md)を使用し、.NET 5 の OS 固有のフレーバーをターゲットとしている場合、ビルドでは、アセンブリレベルの <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> 属性が追加されます。

## <a name="reason-for-change"></a>変更理由

.NET 5.0 Preview 8 で API をサポートするプラットフォームの指定に、<xref:System.Runtime.Versioning> に属性が実装されました。 これらの属性は、プラットフォーム固有の API がそれらの API をサポートしないプラットフォームで使用された場合に、ビルド警告を生成する、[プラットフォーム互換性アナライザー](../../../../core/compatibility/code-analysis.md#ca1416-platform-compatibility)によって使用されます。

.NET 5.0 RC1 では、プラットフォーム互換性アナライザーにプラットフォームを除外する機能が追加されています。 この機能を使用すると、API を OS プラットフォームで完全にサポートされていないものとしてマークできます。 この機能では、より適切な名前を使用するなど、属性への変更が求められています。 不要になった `ObsoletedInOSPlatformAttribute` は、削除されています。

## <a name="version-introduced"></a>導入されたバージョン

5.0 RC1

## <a name="recommended-action"></a>推奨アクション

プロジェクトのターゲットを .NET 5.0 Preview 8 から .NET 5.0 RC1 に変更した場合、これらの変更によりビルド エラーまたは実行時エラーが発生することがあります。 たとえば、`MinimumOSPlatformAttribute` を名前変更すると、エラーが発生する可能性があります。これは、この属性がビルド時にプラットフォーム固有のアセンブリに適用されますが、古い成果物では古い API 名を参照したままであるためです。

ビルド時のエラーの例:

- **エラー CS0246:型または名前空間の名前 'MinimumOSPlatformAttribute' が見つかりませんでした (using ディレクティブまたはアセンブリ参照が指定されていることを確認してください)**
- **エラー CS0246:型または名前空間の名前 'RemovedInOSPlatformAttribute' が見つかりませんでした (using ディレクティブまたはアセンブリ参照が指定されていることを確認してください)**
- **エラー CS0246:型または名前空間の名前 'ObsoletedInOSPlatformAttribute' が見つかりませんでした (using ディレクティブまたはアセンブリ参照が指定されていることを確認してください)**

ランタイム エラーの例:

**未処理の例外。System.TypeLoadException:アセンブリから型 'System.Runtime.Versioning.MinimumOSPlatformAttribute' を読み込むことができませんでした 'System.Runtime, Version=5.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'.**

これらのエラーを解決するには:

- `MinimumOSPlatformAttribute` に対する参照を <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> に更新します。
- `RemovedInOSPlatformAttribute` に対する参照を <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> に更新します。
- `ObsoletedInOSPlatformAttribute` に対する参照を削除します。
- 古いビルド成果物を削除して、自分のプロジェクトをリビルドします (またはクリーンおよびビルドを実行します)。

## <a name="affected-apis"></a>影響を受ける API

- `System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `System.Runtime.Versioning.RemovedInOSPlatformAttribute`

<!--

### Category

Core .NET libraries

### Affected APIs

- `T:System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `T:System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `T:System.Runtime.Versioning.RemovedInOSPlatformAttribute`

-->
