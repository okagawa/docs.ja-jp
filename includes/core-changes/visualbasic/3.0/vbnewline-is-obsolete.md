---
ms.openlocfilehash: 535a73c6b748166a1e4a4661a6bab0671c653278
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721511"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft.VisualBasic.Constants.vbNewLine は古い

<xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> 定数は、.NET Core 3.0 Preview 8 以降では[\[古い\]](xref:System.ObsoleteAttribute)としてマークされています。

#### <a name="version-introduced"></a>導入されたバージョン

3.0 Preview 8

#### <a name="change-description"></a>変更の説明

.NET Core 3.0 Preview 8 以降では、[廃止](xref:System.ObsoleteAttribute)属性が <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> 定数に適用されています。 その定数を使用すると、コンパイラの警告が発生します。 .NET Framework と .NET Core の以前のリリースでは、古いとしてマークされていませんでした。

この変更は、Visual Basic をマルチプラットフォーム開発用の言語としてサポートするために行われました。 <xref:Microsoft.VisualBasic.Constants.vbNewLine> 定数は、Windows での改行文字シーケンスである `\r\n` と同等です。 Unix ベースのシステムでは、改行文字は `\n` です。

#### <a name="recommended-action"></a>推奨アクション

<xref:Microsoft.VisualBasic.Constants.vbNewLine> に対する[廃止](xref:System.ObsoleteAttribute)属性メッセージには、次の推奨事項が含まれています。

キャリッジ リターンとライン フィードの場合は、<xref:Microsoft.VisualBasic.Constants.vbCrLf> を使用します。 現在のプラットフォームの改行の場合は、<xref:System.Environment.NewLine?displayProperty=nameWithType> を使用します。

#### <a name="category"></a>カテゴリ

Visual Basic

#### <a name="affected-apis"></a>影響を受ける API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

#### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
