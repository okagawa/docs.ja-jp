---
title: 破壊的変更:MulticastOption.Group で null 値を受け付けない
description: .NET 5.0 での破壊的変更について学習します。MulticastOption.Group で null 値は受け付けられないようになりました。
ms.date: 08/18/2020
ms.openlocfilehash: 164ac8c2c8dd14f9e0758017e54eeb377f88a7e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759387"
---
# <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a>MulticastOption.Group で null 値を受け付けない

<xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> で `null` の値を受け付けなくなりました。 プロパティを `null` に設定すると、<xref:System.ArgumentNullException> がスローされます。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="change-description"></a>変更の説明

以前のバージョンの .NET では、<xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> プロパティを `null` に設定できます。 <xref:System.Net.Sockets.MulticastOption> が後で <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> に渡される場合、ランタイムによって <xref:System.NullReferenceException> がスローされます。

.NET 5.0 以降では、プロパティを `null` に設定した場合、<xref:System.ArgumentNullException> がスローされます。

## <a name="reason-for-change"></a>変更理由

Framework デザイン ガイドラインとの一貫性を保つため、値が `null` の場合に <xref:System.ArgumentNullException> をスローするようにプロパティは更新されました。

## <a name="recommended-action"></a>推奨アクション

<xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> に `null` を設定していないことを確認します。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

### Category

Networking

-->
