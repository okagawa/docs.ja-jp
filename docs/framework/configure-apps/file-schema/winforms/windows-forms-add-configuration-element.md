---
title: 構成要素の追加 Windows フォーム
ms.date: 04/07/2017
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
ms.openlocfilehash: 26b806f84c3e1bc44e0437a8f8806316b14897b8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "73109658"
---
# <a name="windows-forms-add-configuration-element"></a>構成要素の追加 Windows フォーム

要素は、 `<add>` .NET Framework 4.7 以降の Windows フォームアプリに追加された機能を Windows フォームアプリでサポートするかどうかを指定する定義済みのキーを追加します。

## <a name="syntax"></a>構文

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="key-name" value="key-value" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

| 属性 | 説明 |
| --------- | ----------- |
| `key`     | 必須の属性です。 カスタマイズ可能な特定の機能に対応する定義済みのキー名 Windows フォームます。 |
| `value`   | 必須の属性です。 `key` に代入する値。 |

### <a name="key-attribute-names-and-associated-values"></a>`key`属性名と関連付けられた値

| `key` 名 | 値 | 説明 |
| ---------- | ------ | ----------- |
| "AnchorLayout. Disablesinglepass Controlscaling" | "true" &#124; "false" | 固定されたコントロールを1回のパスで拡大縮小するかどうかを示します。 シングルパスのスケーリングを無効にする場合は "true"。それ以外の場合は false。 詳細については、「[解説](#remarks)」の「シングルパススケール」セクションを参照してください。 |
| "DpiAwareness" | "PerMonitorV2" &#124; "false" | アプリケーションが DPI 対応であるかどうかを示します。 Dpi 認識をサポートするには、キーを "PerMonitorV2" に設定します。それ以外の場合は、"false" に設定します。 DPI 認識はオプトイン機能です。Windows フォームの高 DPI サポートを利用するには、その値を "PerMonitorV2" に設定する必要があります。 詳細については、「[解説](#remarks)」を参照してください。 |
| "CheckedListBox の機能強化" | "true" &#124; "false" | <xref:System.Windows.Forms.CheckedListBox>.NET Framework 4.7 で導入されたスケーリングとレイアウトの改善をコントロールが活用するかどうかを示します。 スケーリングとレイアウトの改善をオプトアウトする場合は "true"。それ以外の場合は、"false" です。 |
| "DataGridView. DisableHighDpiImprovements" | "true" &#124; "false" | <xref:System.Windows.Forms.DataGridView>.NET Framework 4.7 で導入されたコントロールのスケーリングとレイアウトの機能強化を示します。 "true" を選択して DPI 認識を解除します。それ以外の場合は "false"。 |
| "DisableDpiChangedMessageHandling" | "true" &#124; "false" | DPI スケーリングの変更に関連するメッセージの受信をオプトアウトする場合は "true"。それ以外の場合は "false"。 詳細については、「[解説](#remarks)」を参照してください。 |
| "EnableWindowsFormsHighDpiAutoResizing" | "true" &#124; "false" | DPI スケールの変更によって Windows フォームアプリケーションのサイズが自動的に変更されるかどうかを示します。 自動サイズ変更を有効にする場合は "true"。それ以外の場合は false。 |
| "Form. Disablesinglepass Controlscaling" | "true" &#124; "false" | <xref:System.Windows.Forms.Form>が1回のパスでスケーリングされているかどうかを示します。 シングルパススケーリングを無効にする場合は "true"。それ以外の場合は false。 詳細については、「[解説](#remarks)」の「シングルパススケール」セクションを参照してください。 |
| "MonthCalendar. Disablesinglepass Controlscaling" | "true" &#124; "false" | <xref:System.Windows.Forms.MonthCalendar>コントロールが1回のパスでスケーリングされるかどうかを示します。 シングルパススケーリングを無効にする場合は "true"。それ以外の場合は false。 詳細については、「[解説](#remarks)」の「シングルパススケール」セクションを参照してください。 |
| "Toolstrip. DisableHighDpiImprovements" | "true" &#124; "false" | <xref:System.Windows.Forms.ToolStrip>.NET Framework 4.7 で導入されたスケーリングとレイアウトの改善をコントロールが活用するかどうかを示します。 "true" を選択して DPI 認識を解除します。それ以外の場合は "false"。 |

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

| 要素 | Description |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](index.md) | 新しい Windows フォームアプリケーション機能のサポートを構成します。 |

## <a name="remarks"></a>解説

.NET Framework 4.7 を使用すれば、.NET Framework の最近のリリースで追加された機能が利用できる Windows フォームのアプリケーションを、`<System.Windows.Forms.ApplicationConfigurationSection>` 要素で構成できます。

`<System.Windows.Forms.ApplicationConfigurationSection>`要素を使用すると、1つまたは複数の子要素を追加でき `<add>` ます。各子要素は、特定の構成設定を定義します。

高 DPI サポート Windows フォームの概要については、「 [Windows フォームの高 Dpi サポート](../../../winforms/high-dpi-support-in-windows-forms.md)」を参照してください。

### <a name="dpiawareness"></a>DpiAwareness

Windows 10 の作成者エディションと .NET Framework 4.7 以降の .NET Framework のターゲットバージョンで実行される Windows フォームアプリは、.NET Framework 4.7 で導入された高 DPI の機能強化を利用するように構成できます。 これには以下が含まれます。

- Windows フォームアプリケーションの起動後にユーザーが DPI またはスケールファクターを変更する動的な DPI シナリオのサポート。

- コントロールやコントロールなど、多数の Windows フォームコントロールのスケーリングとレイアウトの機能強化 <xref:System.Windows.Forms.MonthCalendar> <xref:System.Windows.Forms.CheckedListBox> 。

高 DPI 認識はオプトイン機能です。既定では、の値 `DpiAwareness` は `false` です。 アプリケーション構成ファイルでこのキーの値をに設定することにより、Windows フォーム ' DPI 対応のサポートを有効にすることができ `PerMonitorV2` ます。 DPI 認識が有効になっている場合は、すべての個別の DPI 機能も有効になります。 これには以下が含まれます。

- DPI 変更メッセージ。キーによって制御され `DisableDpiChangedMessageHandling` ます。

- 動的 DPI サポート。キーによって制御され `EnableWindowsFormsHighDpiAutoResizing` ます。

- 個々のコントロールに対して、固定された `Form.DisableSinglePassControlScaling` <xref:System.Windows.Forms.Form> `AnchorLayout.DisableSinglePassControlScaling` コントロールのキー、および `MonthCalendar.DisableSinglePassControlScaling` コントロールのキー <xref:System.Windows.Forms.MonthCalendar> によって制御される、シングルパスコントロールのスケーリング。

- 高 DPI スケーリングとレイアウトの改善。コントロールのキー、コントロールのキー、 `CheckListBox.DisableHighDpiImprovements` <xref:System.Windows.Forms.CheckedListBox> `DataGridView.DisableHighDpiImprovements` <xref:System.Windows.Forms.DataGridView> および `Toolstrip.DisableHighDpiImprovements` コントロールのキー <xref:System.Windows.Forms.ToolStrip> によって制御されます。

をに設定して指定した単一の既定のオプトイン設定は、 `DpiAwareness` `PerMonitorV2` 通常、新しい Windows フォームアプリケーションに適しています。 ただし、対応するキーをアプリケーション構成ファイルに追加することで、個々の高 DPI 向上を無効にすることができます。 たとえば、動的な DPI サポートを除き、すべての新しい DPI 機能を利用するには、アプリケーション構成ファイルに次のコードを追加します。

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <!-- Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

通常は、プログラムで処理することを選択したため、特定の機能を無効にします。

Windows フォームアプリケーションで高 DPI サポートを利用する方法の詳細については、「 [Windows フォームでの高 Dpi サポート](../../../winforms/high-dpi-support-in-windows-forms.md)」を参照してください。

### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

.NET Framework 4.7 以降、Windows フォームコントロールは、DPI スケーリングの変更に関連する多数のイベントを発生させます。 これには <xref:System.Windows.Forms.Control.DpiChangedAfterParent> 、、、およびの各イベントが含ま <xref:System.Windows.Forms.Control.DpiChangedBeforeParent> <xref:System.Windows.Forms.Form.DpiChanged> れます。 キーの値によって、 `DisableDpiChangedMessageHandling` これらのイベントが Windows フォームアプリケーションで発生するかどうかが決定されます。

### <a name="single-pass-scaling"></a>シングルパススケーリング

単一または複数パスのスケーリングは、ユーザーインターフェイスの認識される応答性と、スケーリングされたユーザーインターフェイス要素の視覚的な外観に影響します。 .NET Framework 4.7 以降では、Windows フォームは1つのパスのスケーリングを使用します。 以前のバージョンの .NET Framework では、複数のパスを使用してスケーリングが実行され、いくつかのコントロールが必要以上に拡大されました。 シングルパススケーリングは、アプリが古い動作に依存している場合にのみ無効にする必要があります。

## <a name="see-also"></a>関連項目

- [Windows フォームの構成セクション](index.md)
- [Windows フォームでの高 DPI サポート](../../../winforms/high-dpi-support-in-windows-forms.md)
