---
ms.openlocfilehash: bba74f26eafd52b966928835d5003d03af1eabdc
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721422"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>DoNotSupportSelectAllShortcutInMultilineTextBox 互換性スイッチはサポートされていません

.NET Framework 4.6.1 で導入された `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` 互換スイッチは、.NET Core 3.0 上の Windows フォームではサポートされていません。

#### <a name="change-description"></a>変更の説明

.NET Framework 4.6.1 以降、<xref:System.Windows.Forms.TextBox> コントロールで <kbd>Ctrl</kbd> + <kbd>A</kbd> ショートカット キーを押すと、すべてのテキストが選択されるようになりました。 .NET Framework 4.6 およびそれ以前のバージョンでは、[Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) および <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> プロパティが `true` に選択されていた場合、<kbd>Ctrl</kbd> + <kbd>A</kbd> ショートカット キーを選択してもすべてのテキストが選択されませんでした。 `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` 互換性スイッチは、元の動作を保持するために .NET Framework 4.6.1 で導入されました。 詳細については、「<xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>」を参照してください。

.NET Core では、`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` スイッチはサポートされていません。

#### <a name="version-introduced"></a>導入されたバージョン

3.0 Preview 9

#### <a name="recommended-action"></a>推奨アクション

スイッチを削除します。 そのスイッチはサポートされておらず、代替機能はありません。

#### <a name="category"></a>カテゴリ

Windows フォーム

#### <a name="affected-apis"></a>影響を受ける API

- None

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
