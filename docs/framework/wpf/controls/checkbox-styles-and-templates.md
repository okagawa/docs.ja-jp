---
title: CheckBox のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], CheckBox
- templates [WPF], CheckBox
- parts [WPF], CheckBox
- ControlTemplate [WPF], CheckBox
- CheckBox [WPF], styles and templates
- styles [WPF], CheckBox
ms.assetid: bfdaec96-d101-4d3d-864d-c27e6b621d03
ms.openlocfilehash: b9eee48c01f53e12bbe4a72f84c20eab68d5de23
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283811"
---
# <a name="checkbox-styles-and-templates"></a>CheckBox のスタイルとテンプレート
このトピックでは、<xref:System.Windows.Controls.CheckBox> コントロールのスタイルとテンプレートについて説明します。 <xref:System.Windows.Controls.ControlTemplate>の既定値を変更して外観を制御します。 詳細については、「[コントロールのためにテンプレートを作成する](../../../desktop-wpf/themes/how-to-create-apply-template.md)」をご覧ください。  
  
## <a name="checkbox-parts"></a>CheckBox のパーツ  
 <xref:System.Windows.Controls.CheckBox> コントロールに名前付きパーツはありません。  
  
## <a name="checkbox-states"></a>CheckBox の状態  
 次の表は、<xref:System.Windows.Controls.CheckBox> コントロールの表示状態の一覧を示します。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|----------------------|---------------------------|-----------------|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されています。|  
|押されている|CommonStates|コントロールが押されています。|  
|無効|CommonStates|コントロールが無効になっています。|  
|フォーカスされている|FocusStates|コントロールにフォーカスがあります。|  
|フォーカスされていない|FocusStates|コントロールにフォーカスがありません。|  
|チェック済み|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> が `true`です。|  
|オフ|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> が `false`です。|  
|Indeterminate|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> が `true` で、<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> が `null` です。|  
|有効|ValidationStates|このコントロールで <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは `false` です。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは、コントロールにフォーカスがある `true` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは、コントロールにフォーカスがない `true` です。|  
  
## <a name="checkbox-controltemplate-example"></a>CheckBox の ControlTemplate の例  
 次の例は、<xref:System.Windows.Controls.CheckBox> コントロールの <xref:System.Windows.Controls.ControlTemplate> を定義する方法を示しています。  
  
 [!code-xaml[ControlTemplateExamples#CheckBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/checkbox.xaml#checkbox)]  
  
 前の例では、次のリソースの 1 つ以上を使用します。  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [コントロールのスタイルとテンプレート](control-styles-and-templates.md)
- [コントロールのカスタマイズ](control-customization.md)
- [スタイルとテンプレート](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [コントロールのためのテンプレートを作成する](../../../desktop-wpf/themes/how-to-create-apply-template.md)
