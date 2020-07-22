---
title: Windows フォームと WPF プロパティの割り当て
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- property mapping [WPF interoperability]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
ms.openlocfilehash: 45d86ac1b65306c8f404f9cea1e663b67128ebc4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794070"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Windows フォームと WPF プロパティの割り当て
Windows フォームと [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] テクノロジには、似ていますが異なる 2 つのプロパティ モデルがあります。 "*プロパティ マッピング*" は、2 つのアーキテクチャ間の相互運用をサポートし、次の機能を提供しています。  
  
- ホスト環境内の関連するプロパティの変更を、ホストされているコントロールまたは要素に簡単にマップすることができます。  
  
- よく使用されるプロパティ マッピングには既定の処理が用意されています。  
  
- 既定のプロパティを簡単に削除、上書き、または拡張できます。  
  
- ホスト上のプロパティ値の変更が自動的に確実に検出され、ホストされているコントロールまたは要素に変換されます。  
  
> [!NOTE]
> プロパティ変更イベントは、ホスティング コントロールまたは要素の階層に伝達されません。 直接設定、スタイル、継承、データ バインディング、またはプロパティの値を変更するその他のメカニズムのために、プロパティのローカル値が変更されない場合、プロパティの変換は実行されません。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素に対して <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> プロパティ、<xref:System.Windows.Forms.Integration.ElementHost> コントロールに対して <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> プロパティを使用して、プロパティ マッピングにアクセスします。  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>WindowsFormsHost 要素を使用したプロパティ マッピング  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素では、次の変換テーブルを使用して、既定の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティを対応する Windows フォームに変換します。  
  
|Windows Presentation Foundation のホスティング|Windows フォーム|相互運用動作|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素を使用して、ホストされているコントロールの <xref:System.Windows.Forms.Control.BackColor%2A> プロパティとホストされているコントロールの <xref:System.Windows.Forms.Control.BackgroundImage%2A> プロパティを設定します。 マッピングは、次の規則を使用して実行されます。<br /><br /> -   <xref:System.Windows.Controls.Control.Background%2A> が純色の場合、変換され、ホストされているコントロールの <xref:System.Windows.Forms.Control.BackColor%2A> プロパティを設定するために使用されます。 ホストされているコントロールには <xref:System.Windows.Forms.Control.BackColor%2A> プロパティの値を継承できるため、ホストされているコントロールに <xref:System.Windows.Forms.Control.BackColor%2A> プロパティは設定されません。 **注:** ホストされているコントロールは透明度をサポートしていません。 <xref:System.Windows.Forms.Control.BackColor%2A> に割り当てられる色は完全に不透明で、アルファ値が 0xFF である必要があります。 <br /><br /> -   <xref:System.Windows.Controls.Control.Background%2A> が純色でない場合、<xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールによって <xref:System.Windows.Controls.Control.Background%2A> プロパティからビットマップが作成されます。 <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールを使用して、このビットマップをホストされているコントロールの <xref:System.Windows.Forms.Control.BackgroundImage%2A> プロパティに割り当てます。 これにより、透明度に似た効果が得られます。 **注:** この動作をオーバーライドするか、<xref:System.Windows.Controls.Control.Background%2A> プロパティ マッピングを削除することができます。|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|既定のマッピングが再割り当てされていない場合、<xref:System.Windows.FrameworkElement.Cursor%2A> プロパティが設定された先祖が見つかるまで、<xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールによって先祖の階層が走査されます。 この値は、対応する最も近い Windows フォーム カーソルに変換されます。<br /><br /> <xref:System.Windows.FrameworkElement.ForceCursor%2A> プロパティの既定のマッピングが再割り当てされていない場合、走査は <xref:System.Windows.FrameworkElement.ForceCursor%2A> が `true` に設定された最初の先祖で停止します。|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight> は <xref:System.Windows.Forms.RightToLeft.No> にマップされます。<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft> は <xref:System.Windows.Forms.RightToLeft.Yes> にマップされます。<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit> はマップされません。<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> は <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType> にマップされます。|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|ホストされているコントロールの <xref:System.Drawing.Font?displayProperty=nameWithType> 上の <xref:System.Drawing.Font.Style%2A>|一連の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティは、対応する <xref:System.Drawing.Font> に変換されます。 これらのプロパティのいずれかが変更されると、新しい <xref:System.Drawing.Font> が作成されます。 <xref:System.Windows.FontStyles.Normal%2A> の場合: <xref:System.Drawing.FontStyle.Italic> は無効です。 <xref:System.Windows.FontStyles.Italic%2A> または <xref:System.Windows.FontStyles.Oblique%2A> の場合: <xref:System.Drawing.FontStyle.Italic> は有効です。|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|ホストされているコントロールの <xref:System.Drawing.Font?displayProperty=nameWithType> 上の <xref:System.Drawing.Font.Style%2A>|一連の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティは、対応する <xref:System.Drawing.Font> に変換されます。 これらのプロパティのいずれかが変更されると、新しい <xref:System.Drawing.Font> が作成されます。 <xref:System.Windows.FontWeights.Black%2A>、<xref:System.Windows.FontWeights.Bold%2A>、<xref:System.Windows.FontWeights.DemiBold%2A>、<xref:System.Windows.FontWeights.ExtraBold%2A>、<xref:System.Windows.FontWeights.Heavy%2A>、<xref:System.Windows.FontWeights.Medium%2A>、<xref:System.Windows.FontWeights.SemiBold%2A>、または <xref:System.Windows.FontWeights.UltraBold%2A> の場合: <xref:System.Drawing.FontStyle.Bold> は有効です。 <xref:System.Windows.FontWeights.ExtraLight%2A>、<xref:System.Windows.FontWeights.Light%2A>、<xref:System.Windows.FontWeights.Normal%2A>、<xref:System.Windows.FontWeights.Regular%2A>、<xref:System.Windows.FontWeights.Thin%2A>、または <xref:System.Windows.FontWeights.UltraLight%2A> の場合: <xref:System.Drawing.FontStyle.Bold> は無効です。|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|一連の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティは、対応する <xref:System.Drawing.Font> に変換されます。 これらのプロパティのいずれかが変更されると、新しい <xref:System.Drawing.Font> が作成されます。 ホストされている Windows フォーム コントロールによって、フォント サイズに基づいてサイズが変更されます。<br /><br /> フォント サイズは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では 96 分の 1 インチとして表され、Windows フォームでは 72 分の 1 インチとして表されます。 対応する変換は次のとおりです。<br /><br /> Windows フォーム フォント サイズ = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] フォント サイズ * 72.0 / 96.0。|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Foreground%2A> プロパティ マッピングは、次の規則を使用して実行されます。<br /><br /> -   <xref:System.Windows.Controls.Control.Foreground%2A> が <xref:System.Windows.Media.SolidColorBrush> の場合は、<xref:System.Windows.Forms.Control.ForeColor%2A> に <xref:System.Windows.Media.SolidColorBrush.Color%2A> を使用します。<br />-   <xref:System.Windows.Controls.Control.Foreground%2A> が <xref:System.Windows.Media.GradientBrush> の場合は、<xref:System.Windows.Forms.Control.ForeColor%2A> の最小オフセット値を持つ <xref:System.Windows.Media.GradientStop> の色を使用します。<br />-   その他の <xref:System.Windows.Media.Brush> の種類の場合、<xref:System.Windows.Forms.Control.ForeColor%2A> は変更されません。 これは、既定値が使用されることを意味します。|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A> が設定されている場合、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素によって、ホストされているコントロールに <xref:System.Windows.Forms.Control.Enabled%2A> プロパティが設定されます。|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|ホストされている Windows フォーム コントロールの <xref:System.Windows.Forms.Control.Padding%2A> プロパティの 4 つの値はすべて、同じ <xref:System.Windows.Thickness> 値に設定されています。<br /><br /> -   <xref:System.Int32.MaxValue> より大きい値は <xref:System.Int32.MaxValue> に設定されます。<br />-   <xref:System.Int32.MinValue> 未満の値は <xref:System.Int32.MinValue> に設定されます。|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible> は <xref:System.Windows.Forms.Control.Visible%2A> = `true` にマップされます。 ホストされている Windows フォーム コントロールが表示されます。 ホストされているコントロールの <xref:System.Windows.Forms.Control.Visible%2A> プロパティを明示的に `false` に設定することはお勧めしません。<br />-   <xref:System.Windows.Visibility.Collapsed> は <xref:System.Windows.Forms.Control.Visible%2A> = `true` または `false` にマップされます。 ホストされている Windows フォーム コントロールは描画されず、その領域は折りたたまれます。<br />-   <xref:System.Windows.Visibility.Hidden> :ホストされている Windows フォーム コントロールはレイアウトの領域を占有しますが、表示されません。 この場合、<xref:System.Windows.Forms.Control.Visible%2A> プロパティは `true` に設定されます。 ホストされているコントロールの <xref:System.Windows.Forms.Control.Visible%2A> プロパティを明示的に `false` に設定することはお勧めしません。|  
  
 コンテナー要素の添付プロパティは、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素によって完全にサポートされています。  
  
 詳細については、「[チュートリアル:WindowsFormsHost 要素を使用したプロパティ マッピング](walkthrough-mapping-properties-using-the-windowsformshost-element.md)」を参照してください。  
  
## <a name="updates-to-parent-properties"></a>親プロパティの更新  
 ほとんどの親プロパティを変更すると、ホストされている子コントロールに通知が送信されます。 次の一覧では、値が変更されても通知されないプロパティについて説明します。  
  
- <xref:System.Windows.Controls.Control.Background%2A>  
  
- <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
- <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
- <xref:System.Windows.UIElement.Visibility%2A>  
  
 たとえば、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素の <xref:System.Windows.Controls.Control.Background%2A> プロパティの値を変更しても、ホストされているコントロールの <xref:System.Windows.Forms.Control.BackColor%2A> プロパティは変更されません。  
  
## <a name="property-mapping-with-the-elementhost-control"></a>ElementHost コントロールを使用したプロパティ マッピング  
 次のプロパティには、組み込みの変更通知が用意されています。 これらのプロパティをマッピングするときは、<xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> メソッドを呼び出さないでください。  
  
- AutoSize  
  
- BackColor  
  
- BackgroundImage  
  
- BackgroundImageLayout  
  
- BindingContext  
  
- CausesValidation  
  
- ContextMenu  
  
- ContextMenuStrip  
  
- カーソル  
  
- ドッキング  
  
- 有効  
  
- フォント  
  
- 前景色  
  
- 場所  
  
- 余白  
  
- [間隔]  
  
- 親  
  
- Region  
  
- RightToLeft  
  
- サイズ  
  
- TabIndex  
  
- TabStop  
  
- テキスト  
  
- Visible  
  
 <xref:System.Windows.Forms.Integration.ElementHost> コントロールでは、次の変換テーブルを使用して、既定の Windows フォーム プロパティを同等の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に変換します。  
  
 詳細については、「[チュートリアル:ElementHost コントロールを使用したプロパティ マッピング](walkthrough-mapping-properties-using-the-elementhost-control.md)」を参照してください。  
  
|Windows フォームのホスティング|Windows Presentation Foundation|相互運用動作|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> ホストされている要素に対する (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)。|このプロパティを設定すると、<xref:System.Windows.Media.ImageBrush> が強制的に再描画されます。 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> プロパティが `false` (既定値) に設定されている場合、この <xref:System.Windows.Media.ImageBrush> は、その <xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.BackgroundImage%2A>、<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> プロパティを含む <xref:System.Windows.Forms.Integration.ElementHost> コントロールの外観と、アタッチされているすべてのペイント ハンドラーに基づいています。<br /><br /> <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> プロパティが `true` に設定されている場合、<xref:System.Windows.Media.ImageBrush> は、親の <xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.BackgroundImage%2A>、<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> プロパティを含む <xref:System.Windows.Forms.Integration.ElementHost> コントロールの親の外観と、アタッチされているペイント ハンドラーに基づいています。|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> ホストされている要素に対する (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)。|このプロパティを設定すると、<xref:System.Windows.Forms.Control.BackColor%2A> のマッピングについて説明したものと同じ動作が発生します。|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> ホストされている要素に対する (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)。|このプロパティを設定すると、<xref:System.Windows.Forms.Control.BackColor%2A> のマッピングについて説明したものと同じ動作が発生します。|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|Windows フォーム標準カーソルは、対応する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 標準カーソルに変換されます。 Windows フォームが標準カーソルでない場合は、既定値が割り当てられます。|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A> が設定されている場合、<xref:System.Windows.Forms.Integration.ElementHost> コントロールによって、ホストされている要素に <xref:System.Windows.UIElement.IsEnabled%2A> プロパティが設定されます。|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A> の値は、対応する一連の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] フォント プロパティに変換されます。|  
|<xref:System.Drawing.Font.Bold%2A>|ホストされている要素に対する <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Bold%2A> が `true` の場合、<xref:System.Windows.Controls.Control.FontWeight%2A> が <xref:System.Windows.FontWeights.Bold%2A> に設定されます。<br /><br /> <xref:System.Drawing.Font.Bold%2A> が `false` の場合、<xref:System.Windows.Controls.Control.FontWeight%2A> が <xref:System.Windows.FontWeights.Normal%2A> に設定されます。|  
|<xref:System.Drawing.Font.Italic%2A>|ホストされている要素に対する <xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Italic%2A> が `true` の場合、<xref:System.Windows.Controls.Control.FontStyle%2A> が <xref:System.Windows.FontStyles.Italic%2A> に設定されます。<br /><br /> <xref:System.Drawing.Font.Italic%2A> が `false` の場合、<xref:System.Windows.Controls.Control.FontStyle%2A> が <xref:System.Windows.FontStyles.Normal%2A> に設定されます。|  
|<xref:System.Drawing.Font.Strikeout%2A>|ホストされている要素に対する <xref:System.Windows.TextDecorations>|<xref:System.Windows.Controls.TextBlock> コントロールをホストする場合にのみ適用されます。|  
|<xref:System.Drawing.Font.Underline%2A>|ホストされている要素に対する <xref:System.Windows.TextDecorations>|<xref:System.Windows.Controls.TextBlock> コントロールをホストする場合にのみ適用されます。|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No> は <xref:System.Windows.FlowDirection.LeftToRight> にマップされます。<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes> は <xref:System.Windows.FlowDirection.RightToLeft> にマップされます。|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Integration.ElementHost> コントロールでは、次の規則を使用して、ホストされている要素に <xref:System.Windows.UIElement.Visibility%2A> プロパティを設定します。<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true` は <xref:System.Windows.Visibility.Visible> にマップされます。<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false` は <xref:System.Windows.Visibility.Hidden> にマップされます。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF と Win32 の相互運用性](wpf-and-win32-interoperation.md)
- [WPF と Windows フォームの相互運用性](wpf-and-windows-forms-interoperation.md)
- [チュートリアル: WindowsFormsHost 要素を使用したプロパティ マッピング](walkthrough-mapping-properties-using-the-windowsformshost-element.md)
- [チュートリアル: ElementHost コントロールを使用したプロパティ マッピング](walkthrough-mapping-properties-using-the-elementhost-control.md)
