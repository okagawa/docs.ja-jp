---
ms.openlocfilehash: 27c6353f8f71254a505b434921f4b1e61e64cdda
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2021
ms.locfileid: "98758165"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>FolderBrowserDialog の最新化

<xref:System.Windows.Forms.FolderBrowserDialog> コントロールが、.NET Core の Windows フォーム アプリケーションで変更されています。

#### <a name="change-description"></a>変更の説明

.NET Framework で Windows フォームは <xref:System.Windows.Forms.FolderBrowserDialog> コントロールに対し、次のダイアログを使用します。

![.NET Framework の FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

.NET Core 3.0 では、Windows フォームにより、Windows Vista で導入された次の新しい COM ベースのコントロールが使用されます。

![.NET Core の FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="recommended-action"></a>推奨アクション

このダイアログは、自動的にアップグレードされます。

元のダイアログを保持したい場合、ダイアログを表示する前に、次のコード断片で示されるとおり、<xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> プロパティを `false` に設定します。

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a>カテゴリ

Windows フォーム

#### <a name="affected-apis"></a>影響を受ける API

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

#### Affected APIs

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
