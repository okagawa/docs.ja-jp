---
ms.openlocfilehash: 56127309c5f5993ffc2e2faedd1f481e8131e094
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400636"
---
### <a name="textformatflagsmodifystring-is-obsolete"></a>TextFormatFlags.ModifyString は古くなっています

<xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> フィールドには警告として非推奨マークが付いています。今後の .NET バージョンで削除される可能性があります。

#### <a name="change-description"></a>変更の説明

以前のバージョンの .NET では、<xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> 列挙フィールドは非推奨になっていません。 .NET 5.0 以降のバージョンでは、警告として非推奨マークが付いています。 このフィールドは今後の .NET バージョンで削除される可能性があります。

#### <a name="reason-for-change"></a>変更理由

<xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> で <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> に文字列を渡すと、その文字列が変化することがあります。 この動作は文字列の不変性という約束事を破るものであり、.NET ランタイムが致命的に破損するおそれがあります。

#### <a name="version-introduced"></a>導入されたバージョン

.NET 5.0 RC1

#### <a name="recommended-action"></a>推奨アクション

<xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> に依存するコードがあれば、それを更新します。

#### <a name="category"></a>カテゴリ

Windows フォーム

#### <a name="affected-apis"></a>影響を受ける API

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

#### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

-->
