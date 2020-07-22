---
ms.openlocfilehash: c8e1c91f4fee8aa896b6617c815fe2a4b6d22f2a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614891"
---
### <a name="accessibility-improvements-in-windows-forms-controls"></a>Windows フォーム コントロールでのアクセシビリティの向上

#### <a name="details"></a>説明

Windows フォームはアクセシビリティ テクノロジによってユーザー サポートの動作が向上します。 これには、.NET Framework 4.7.1 以降の次の変更が含まれます。

- ハイ コントラスト モード中の表示が向上する変更。
- プロパティ ブラウザーのエクスペリエンスが向上する変更。 プロパティ ブラウザーについては次のような点が向上します。
- さまざまなドロップダウン選択ウィンドウを利用することでキーボード操作が便利になりました。
- 不要なタブ ストップが減ります。
- コントロールの種類の報告機能が改善されました。
- ナレーターの動作が改善されました。
- コントロールに不足している UI アクセシビリティ パターンを実装する変更。

#### <a name="suggestion"></a>提案される解決策

**これらの変更を選択する方法と選択しない方法** アプリケーションでこれらの変更を利用するには、.NET Framework 4.7.1 以降で実行する必要があります。 アプリケーションは、次のいずれかの方法でこれらの変更を利用できます。

- .NET Framework 4.7.1 を対象にして再コンパイルします。 .NET Framework 4.7.1 以降を対象とする Windows フォーム アプリケーションでは、これらのアクセシビリティの変更が既定で有効になります。
- 下の例のように、app.config ファイルの `<runtime>` セクションに次の [AppContext スイッチ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)を追加し、それを `false` に設定することで、以前のアクセシビリティ動作を無効にします。

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
  </runtime>
</configuration>
```

.NET Framework 4.7.1 以降を対象とするアプリケーションで以前のアクセシビリティ動作を残す場合、この AppContext スイッチを明示的に `true` に設定することで以前のアクセシビリティ機能を選択できます。<p/>UI オートメーションの概要については、「[UI オートメーションの概要](~/docs/framework/ui-automation/ui-automation-overview.md)」を参照してください。<p/>**UI オートメーション パターンとプロパティに対して追加されたサポート**<br/>アクセシビリティ クライアントは、一般的なパブリックに記述された呼び出しパターンを使って、新しい WinForms アクセシビリティ機能を利用できます。 これらのパターンは、WinForms に固有ではありません。 たとえば、アクセシビリティ クライアントは、IAccessible インターフェイス (MAAS) の QueryInterface メソッドを呼び出して、IServiceProvider インターフェイスを取得することができます。 このインターフェイスを使用できる場合、クライアントはその QueryService メソッドを使って、IAccessibleEx インターフェイスを要求できます。 詳しくは、「[Using IAccessibleEx from a Client](https://docs.microsoft.com/windows/desktop/WinAuto/using-iaccessibleex-from-a-client)」(クライアントからの IAccessibleEx の使用) をご覧ください。 .NET Framework 4.7.1 以降では、IServiceProvider と [IAccessibleEx](https://docs.microsoft.com/windows/desktop/WinAuto/iaccessibleex) (該当する場合) を WinForms ユーザー補助オブジェクトで使用できます。<p/>.NET Framework 4.7.1 では、次の UI オートメーション パターンやプロパティのサポートが追加されます。

- <xref:System.Windows.Forms.ToolStripSplitButton> および <xref:System.Windows.Forms.ComboBox> コントロールは、[展開/折りたたみパターン](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)をサポートします。
- <xref:System.Windows.Forms.ToolStripMenuItem> コントロールの [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) プロパティの値は <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType> です。
- <xref:System.Windows.Forms.ToolStripItem> コントロールは、<xref:System.Windows.Automation.AutomationElement.NameProperty> プロパティと[展開/折りたたみパターン](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)をサポートします。
- <xref:System.Windows.Forms.ToolStripDropDownItem> コントロールは、ドロップダウンが展開されたり折りたたまれたりしたときの StateChange と NameChange を示す <xref:System.Windows.Forms.AccessibleEvents> をサポートします。
- <xref:System.Windows.Forms.ToolStripDropDownButton> コントロールの [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) プロパティの値は <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType> です。
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell> コントロールは <xref:System.Windows.Automation.TogglePattern> をサポートします。
- <xref:System.Windows.Forms.NumericUpDown> および <xref:System.Windows.Forms.DomainUpDown> コントロールは <xref:System.Windows.Automation.AutomationElement.NameProperty> プロパティをサポートし、[ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md) は <xref:System.Windows.Automation.ControlType.Spinner?displayProperty=nameWithType> です。</p>
**PropertyGrid コントロールの向上** .NET Framework 4.7.1 では、PropertyBrowser コントロールが次のように向上します。

- ユーザーが <xref:System.Windows.Forms.PropertyGrid> コントロールに誤った値を入力すると表示されるエラー ダイアログの **[詳細]** ボタンは、[展開/折りたたみパターン](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)、状態と名前の変更通知、および [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) プロパティの値 <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType> をサポートします。
- エラー ダイアログの **[詳細]** ボタンを展開すると表示されるメッセージ ウィンドウは、キーボードでアクセスできるようになり、エラー メッセージの内容をナレーターで読み上げることができます。
- <xref:System.Windows.Forms.PropertyGrid> コントロールの行の <xref:System.Windows.Forms.AccessibleRole> は、&quot;Row&quot; から &quot;Cell&quot; に変更されました。 セルは UIA の ControlType &quot;DataItem&quot; にマップし、適切なキーボード ショートカットとナレーターの読み上げをサポートすることができます。
- <xref:System.Windows.Forms.PropertyGrid> コントロールの <xref:System.Windows.Forms.PropertyGrid.PropertySort> プロパティが <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> に設定されているときにヘッダー項目を表す <xref:System.Windows.Forms.PropertyGrid> コントロールの行は、[ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) プロパティの値が <xref:System.Windows.Automation.ControlType.Button?displayProperty=nameWithType> です。
- <xref:System.Windows.Forms.PropertyGrid> コントロールの <xref:System.Windows.Forms.PropertyGrid.PropertySort> プロパティが <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> に設定されているときにヘッダー項目を表す <xref:System.Windows.Forms.PropertyGrid> コントロールの行は、[展開/折りたたみパターン](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)をサポートします。
- グリッドとその上にある ToolBar の間のキーボード ナビゲーションが向上します。 &quot;Shift + Tab&quot; キーを押すと、ToolBar 全体ではなく、ToolBar の最初のボタンが選択されるようになりました。
- ハイ コントラスト モードで表示された <xref:System.Windows.Forms.PropertyGrid> コントロールでは、<xref:System.Windows.Forms.PropertyGrid.PropertySort> プロパティの現在の値に対応する ToolBar ボタンの周囲にフォーカス四角形が描画されます。
- ハイ コントラスト モードで表示され、<xref:System.Windows.Forms.PropertyGrid.PropertySort> プロパティが <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> に設定された <xref:System.Windows.Forms.PropertyGrid> コントロールでは、カテゴリ ヘッダーの背景がハイ コントラストの色で表示されます。
- <xref:System.Windows.Forms.PropertyGrid> コントロールでは、フォーカスが設定された ToolBar 項目と、<xref:System.Windows.Forms.PropertyGrid.PropertySort> プロパティの現在の値を示す ToolBar 項目の区別が明確になります。 この修正は、ハイ コントラストの変更と、非ハイ コントラストのシナリオに対する変更で構成されます。
- <xref:System.Windows.Forms.PropertyGrid.PropertySort> プロパティの現在の値を示す <xref:System.Windows.Forms.PropertyGrid> コントロールの ToolBar 項目は、<xref:System.Windows.Automation.TogglePattern> をサポートします。
- 配置ピッカーで選択された配置を区別するナレーターのサポートが向上します。
- 空の <xref:System.Windows.Forms.PropertyGrid> コントロールがフォームに表示されているとき、以前はフォーカスを設定されませんでしたが、現在はフォーカスを設定されるようになっています。

**ハイ コントラスト テーマでの OS で定義された色の使用**

- <xref:System.Windows.Forms.ButtonBase.FlatStyle> プロパティが <xref:System.Windows.Forms.FlatStyle.System?displayProperty=nameWithType> (既定のスタイル) に設定された <xref:System.Windows.Forms.Button> および <xref:System.Windows.Forms.CheckBox> コントロールは、ハイ コントラスト テーマが選択されているときは OS で定義された色を使用するようになりました。 以前は、テキストと背景の色はコントラストが同じで、見分けるのが困難でした。
- <xref:System.Windows.Forms.Control.Enabled> プロパティが **false** に設定された <xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.CheckBox>、<xref:System.Windows.Forms.RadioButton>、<xref:System.Windows.Forms.Label>、<xref:System.Windows.Forms.LinkLabel>、<xref:System.Windows.Forms.GroupBox> コントロールでは、以前は影付きの色を使ってハイ コントラスト テーマのテキストがレンダリングされており、背景に対するコントラストが低くなっていました。 現在は、これらのコントロールは OS によって定義された &quot;無効なテキスト&quot; の色を使うようになっています。 この修正は、`FlatStyle` プロパティが <xref:System.Windows.Forms.FlatStyle.System?displayProperty=nameWithType> 以外の値に設定されたコントロールに適用されます。 後者のコントロールは OS によってレンダリングされます。
- <xref:System.Windows.Forms.DataGridView> では、現在フォーカスが設定されているセルの内容を囲むように目に見える四角形がレンダリングされます。 以前は、特定のハイ コントラスト テーマではこれは見えませんでした。
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled> プロパティが **false** に設定された <xref:System.Windows.Forms.ToolStripMenuItem> コントロールは、OS によって定義された &quot;無効なテキスト&quot; の色を使うようになりました。
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked> プロパティが **true** に設定された <xref:System.Windows.Forms.ToolStripMenuItem> コントロールは、コントラストのあるシステム カラーで関連するチェック マークをレンダリングするようになりました。  以前は、チェック マークの色に十分なコントラストがなく、ハイ コントラスト テーマでは見えませんでした。
注:Windows 10 では、一部のハイ コントラストのシステム カラーの値が変更されています。 Windows フォームのフレームワークは、Win32 フレームワークに基づいています。 最も快適に利用するためには、最新版の Windows で実行し、テスト アプリケーションに app.manifest ファイルを追加して最新の OS 変更を選択し、次のコードのコメントを解除します。

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

**キーボード ナビゲーションの向上**

- <xref:System.Windows.Forms.ComboBox> コントロールの <xref:System.Windows.Forms.ComboBox.DropDownStyle> プロパティが <xref:System.Windows.Forms.ComboBoxStyle.DropDownList?displayProperty=nameWithType> に設定されていて、フォームのタブ オーダーで最初のコントロールである場合、キーボードを使って親フォームが開かれると、コントロールにフォーカスの四角形が表示されるようになりました。 この変更の前は、キーボード フォーカスはこのコントロールに設定されましたが、フォーカス インジケーターはレンダリングされませんでした。

**ナレーター サポートが改善されました**

- <xref:System.Windows.Forms.MonthCalendar> コントロールに、以前は行われなかったナレーターによるコントロールの値の読み上げなど、コントロールにアクセスするための支援技術のサポートが追加されました。

- <xref:System.Windows.Forms.CheckedListBox> コントロールは、<xref:System.Windows.Forms.CheckBox.CheckState?displayProperty=nameWithType> プロパティが変更されるとナレーターに通知するようになりました。 以前は、ナレーターは通知を受け取らなかったため、ユーザーには <xref:System.Windows.Forms.CheckBox.CheckState> プロパティが更新されたことが知らされませんでした。
- <xref:System.Windows.Forms.LinkLabel> コントロールがコントロール内のテキストをナレーターに通知する方法が変更されました。 以前は、ナレーターはこのテキストを 2 回読み上げ、ユーザーには表示されなくても &quot;&amp;&quot; 記号を実際のテキストとして読んでいました。 重複するテキストおよび不要な &quot;&amp;&quot; 記号が、ナレーターの読み上げから除去されました。
- <xref:System.Windows.Forms.DataGridViewCell> コントロールの種類が、読み取り専用の状態をナレーターおよびその他の支援技術に正しくレポートするようになりました。
- ナレーターは、[マルチドキュメント インターフェイス]~/docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md) アプリケーションの子ウィンドウのシステム メニューを読み上げられるようになりました。
- ナレーターは、<xref:System.Windows.Forms.ToolStripItem.Enabled?displayProperty=nameWithType> プロパティが **false** に設定された <xref:System.Windows.Forms.ToolStripMenuItem> コントロールを読み上げられるようになりました。 以前のナレーターは、無効なメニュー項目にフォーカスを設定できず、内容を読み上げることができませんでした。

| 名前    | [値]       |
|:--------|:------------|
| スコープ   | Major       |
| バージョン | 4.8         |
| 種類    | 再ターゲット中 |

#### <a name="affected-apis"></a>影響を受ける API

- <xref:System.Windows.Forms.ToolStripDropDownButton.CreateAccessibilityInstance?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownAccessibleObject.Name?displayProperty=nameWithType>
- [MonthCalendar.AccessibilityObject](xref:System.Windows.Forms.Control.AccessibilityObject)
