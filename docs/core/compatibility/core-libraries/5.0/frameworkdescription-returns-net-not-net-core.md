---
title: '破壊的変更: FrameworkDescription の値が .NET Core ではなく .NET になる'
description: Core .NET ライブラリでの .NET 5.0 に関する破壊的変更について学習します。この変更により、RuntimeInformation.FrameworkDescription は、".NET Core" ではなく、".NET" を返すようになりました。
ms.date: 11/01/2020
ms.openlocfilehash: 3925fb092135c26291e1e60b99f359974d21553c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759831"
---
# <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a>FrameworkDescription の値が .NET Core ではなく .NET になる

<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> によって、".NET Core" ではなく ".NET" が返されるようになりました。

## <a name="change-description"></a>変更内容

以前のバージョンの .NET では、<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> によって、説明文字列の一部として ".NET Core" が返されます。たとえば、`.NET Core 3.1.1` です。

.NET 5.0 以降は、<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> によって、説明文字列の一部として ".NET" が返されます。たとえば、`.NET 5.0.0` です。

## <a name="reason-for-change"></a>変更理由

.NET 5 では、`netcoreapp` は、短いターゲット フレームワーク モニカーとして `net` に置き換えられます。 一貫性を確保するために、フレームワークの説明も更新されています。 `FrameworkName` は <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> プロパティ以外の場所ではエンコードされないため、変更は表面的なものになります。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> によって返される文字列で ".NET Core" を検索するすべてのコードを更新します。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
