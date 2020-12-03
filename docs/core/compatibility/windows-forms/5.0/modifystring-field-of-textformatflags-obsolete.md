---
title: 破壊的変更:TextFormatFlags.ModifyString は古くなっています
description: .NET 5.0 の破壊的変更について学習します。この変更により、TextFormatFlags.ModifyString は警告として古いものとなります。
ms.date: 11/05/2020
ms.openlocfilehash: 83dca65a770ccdcd5ce48bb669f5122dc2d5ad77
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759376"
---
# <a name="textformatflagsmodifystring-is-obsolete"></a>TextFormatFlags.ModifyString は古くなっています

<xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> フィールドには警告として非推奨マークが付いています。今後の .NET バージョンで削除される可能性があります。

## <a name="change-description"></a>変更の説明

以前のバージョンの .NET では、<xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> 列挙フィールドは非推奨になっていません。 .NET 5.0 以降のバージョンでは、警告として非推奨マークが付いています。 このフィールドは今後の .NET バージョンで削除される可能性があります。

## <a name="reason-for-change"></a>変更理由

<xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> で <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> に文字列を渡すと、その文字列が変化することがあります。 この動作は文字列の不変性という約束事を破るものであり、.NET ランタイムが致命的に破損するおそれがあります。

## <a name="version-introduced"></a>導入されたバージョン

.NET 5.0

## <a name="recommended-action"></a>推奨アクション

<xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> に依存するコードがあれば、それを更新します。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

### Category

Windows Forms

-->
