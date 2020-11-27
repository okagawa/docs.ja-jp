---
title: UI オートメーションによる標準コントロールのサポート
description: Windows Presentation Foundation (WPF)、Win32、Windows フォーム用に開発されたアプリケーションの標準コントロールに対する UI オートメーションのサポートに関する情報を入手します。
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 0a5a0b61a6492d9efb62799fa610859b247cf26e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261073"
---
# <a name="ui-automation-support-for-standard-controls"></a>UI オートメーションによる標準コントロールのサポート

> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックで [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] は [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 、、Win32、および Windows フォームフレームワーク用に開発されたアプリケーションの標準コントロールのサポートについて説明します。  
  
<a name="Windows_Presentation_Foundation_Controls"></a>

## <a name="windows-presentation-foundation-controls"></a>Windows Presentation Foundation コントロール  

 ユーザー操作に関する情報やサポートを提供するすべての [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] コントロール要素は、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を全面的にネイティブ サポートしています。 パネルなどのその他の要素は、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]からは認識できません。  
  
<a name="Win32_Controls"></a>

## <a name="win32-controls"></a>Win32 コントロール  

 ほとんどの Win32 コントロールは、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll のクライアント側プロバイダーを介してに公開されます。 このアセンブリは、UI オートメーション クライアント アプリケーションで使用するために、自動的に登録されます。  
  
 完全サポートは、バージョン6の *ComCtrl32.dll* のコントロールに対してのみ提供されます。  
  
 次のコントロールがサポートされています。  
  
|クラス名|コントロール型|  
|----------------|------------------|  
|Button|Button|  
|Button|RadioButton|  
|ボタン|グループ|  
|ボタン|CheckBox|  
|ボタン|ハイパーリンク|  
|ボタン|SplitButton|  
|ボタン|CheckBox|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|編集|ドキュメント|  
|編集|編集|  
|SysLink|ハイパーリンク|  
|静的|テキスト|  
|静的|Image|  
|SysIPAddress32|カスタム|  
|SysHeader32|Header/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|List|  
|ListBox|List|  
|ListBox|ListItem|  
|#32768|メニュー|  
|#32768|MenuItem|  
|msctls_progress32|ProgressBar|  
|RichEdit|ドキュメントです。 「注」を参照してください。|  
|RichEdit20A|ドキュメント|  
|RichEdit20W|ドキュメント|  
|RichEdit50W|ドキュメント|  
|ScrollBar|スライダー|  
|msctls_trackbar32|スライダー|  
|msctls_updown32|Spinner|  
|msctls_statusbar32|StatusBar|  
|SysTabControl32|タブ|  
|SysTabControl32|TabItem|  
|ToolbarWindow32|ToolBar|  
|ToolbarWindow32|MenuItem|  
|ToolbarWindow32|ボタン|  
|ToolbarWindow32|CheckBox|  
|ToolbarWindow32|RadioButton|  
|ToolbarWindow32|区切り記号|  
|tooltips_class32|ToolTip|  
|#32774|ToolTip|  
|ReBarWindow32|ツール バー|  
|SysTreeView32|ツリー|  
|SysTreeView32|TreeItem|  
  
 **メモ** RichEdit コントロールは、Windows Vista に付属しているバージョン (RichEd20.dll バージョン3.1 以降では MsftEdit.dll バージョン4.1 以降) でのみサポートされています。  
  
 次のコントロールはサポートされていません。  
  
|クラス名|コントロール型|  
|----------------|------------------|  
|SysAnimate32|Image|  
|SysPager|Spinner|  
|SysDateTimePick32|カスタム|  
|SysMonthCal32|Calendar|  
|MS_WINNOTE|ヒント|  
|VBBubble|ヒント|  
|ScrollBar (スタンドアロン コントロールとして使用される場合)|スライダー|  
|SuperGrid|カスタム|  
  
<a name="Windows_Forms_Controls"></a>

## <a name="windows-forms-controls"></a>Windows フォーム コントロール  

 Windows フォームコントロールは、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll のクライアント側プロバイダーを介してに公開されます。 このアセンブリは、UI オートメーション クライアント アプリケーションで使用するために、自動的に登録されます。  
  
 通常、Win32 コモンコントロールのマネージラッパーである Windows フォームコントロールは、でサポートされてい [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ます。 次のコントロールがサポートされています。  
  
|Class Name (クラス名)|  
|----------------|  
|ボタン|  
|CheckBox|  
|CheckedListBox|  
|ColorDialog|  
|ComboBox|  
|FolderBrowser|  
|FontDialog|  
|GroupBox|  
|HscrollBar|  
|ImageList|  
|Label|  
|ListBox|  
|ListView|  
|MainMenu/ContextMenu|  
|MonthCalendar|  
|NotifyIcon|  
|OpenFileDialog|  
|PageSetupDialog|  
|PrintDialog|  
|ProgressBar|  
|RadioButton|  
|RichTextBox|  
|SaveFileDialog|  
|ScrollableControl|  
|SoundPlayer|  
|StatusBar|  
|TabControl/TabPage|  
|TextBox|  
|Timer|  
|ツール バー|  
|ToolTip|  
|TrackBar|  
|TreeView|  
|VscrollBar|  
|WebBrowser|  
  
 次のコントロールは、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Microsoft Active Accessibility のサポートを通じてのみに公開されます。 一部の機能が使用できないことがあります。  
  
|コントロール名|  
|------------------|  
|BindingSource|  
|DataGrid|  
|DataGridView|  
|DataNavigator|  
|DomainUpDown|  
|ErrorProvider|  
|FlowLayoutPanel|  
|フォーム|  
|LinkLabel|  
|HelpProvider|  
|MaskedTextBox|  
|MenuStrip/ContextMenuStrip|  
|NumericUpDown|  
|パネル|  
|PictureBox|  
|PrintDocument|  
|PrintPreview-Control|  
|PrintPreview-Dialog|  
|PropertyGrid|  
|UserControl|  
|ToolStrip|  
|TableLayoutPanel|  
|SplitContainer/SplitterPanel|  
|スプリッター|  
|RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション コントロール型](ui-automation-control-types.md)
