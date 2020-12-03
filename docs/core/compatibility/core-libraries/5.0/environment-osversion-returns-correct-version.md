---
title: 破壊的変更:Environment.OSVersion で正しいオペレーティング システム バージョンが返される
description: Environment.OSVersion から、たとえば、アプリケーションの互換性にために選択されている OS ではなく、オペレーティング システムの実際のバージョンが返されるという、コア .NET ライブラリの .NET 5.0 破壊的変更について学習します。
ms.date: 11/01/2020
ms.openlocfilehash: b78ca1c7be50f76b99b5558a976d8f00e2f560c3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760073"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a>Environment.OSVersion で正しいオペレーティング システム バージョンが返される

<xref:System.Environment.OSVersion?displayProperty=nameWithType> で、アプリケーションの互換性のために選択される OS などではなく、オペレーティング システム (OS) の実際のバージョンが返されます。

## <a name="change-description"></a>変更の説明

以前のバージョンの .NET では、アプリケーションが Windows 互換モードで実行されている場合、<xref:System.Environment.OSVersion?displayProperty=nameWithType> によって、正しくない可能性がある OS バージョンが返されます。 詳細については、[GetVersionExA 関数の解説](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks)に関する記述を参照してください。

.NET 5.0 以降では、<xref:System.Environment.OSVersion?displayProperty=nameWithType> によってオペレーティング システムの実際のバージョンが返されます。

## <a name="reason-for-change"></a>変更理由

このプロパティのユーザーは、オペレーティング システムの実際のバージョンが返されることを期待しています。 ほとんどの .NET アプリにより、アプリケーション マニフェストでサポートされているバージョンが指定されないため、dotnet ホストから既定でサポートされているバージョンが取得されます。 その結果、実行されているアプリでは互換性 shim はほとんど意味がなくなります。 Windows で新しいバージョンがリリースされており、古い dotnet ホストがまだ使用されている場合は、これらのアプリの OS バージョンが正しくない可能性があります。 実際のバージョンを返すことが、この API に対する開発者の期待により沿うことになります。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

<xref:System.Environment.OSVersion?displayProperty=nameWithType> を使用するコードを確認してテストし、確実に期待どおりに動作するようにします。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->
