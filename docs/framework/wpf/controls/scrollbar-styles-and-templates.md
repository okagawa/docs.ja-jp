---
title: ScrollBar のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
ms.openlocfilehash: 7093a78555aefd73f9bb05c0a7b5fab6b66176fc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283408"
---
# <a name="scrollbar-styles-and-templates"></a>ScrollBar のスタイルとテンプレート
このトピックでは、<xref:System.Windows.Controls.Primitives.ScrollBar> コントロールのスタイルとテンプレートについて説明します。 <xref:System.Windows.Controls.ControlTemplate>の既定値を変更して外観を制御します。 詳細については、「[コントロールのためにテンプレートを作成する](../../../desktop-wpf/themes/how-to-create-apply-template.md)」をご覧ください。  
  
## <a name="scrollbar-parts"></a>ScrollBar のパーツ  
 次の表は、<xref:System.Windows.Controls.Primitives.ScrollBar> コントロールの名前付きパーツの一覧を示します。  
  
|パーツ|種類|説明|  
|-|-|-|  
|PART_Track|<xref:System.Windows.Controls.Primitives.Track>|<xref:System.Windows.Controls.Primitives.ScrollBar> の位置を示す要素のコンテナー。|  
  
## <a name="scrollbar-states"></a>ScrollBar の状態  
 次の表は、<xref:System.Windows.Controls.Primitives.ScrollBar> コントロールの表示状態の一覧を示します。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|----------------------|---------------------------|-----------------|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されます。|  
|無効|CommonStates|コントロールが無効になっています。|  
|有効|ValidationStates|このコントロールで <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは `true` で、コントロールにフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは `true` で、コントロールにフォーカスがありません。|  
  
## <a name="scrollbar-controltemplate-example"></a>ScrollBar の ControlTemplate の例  
 次の例は、<xref:System.Windows.Controls.Primitives.ScrollBar> コントロールの <xref:System.Windows.Controls.ControlTemplate> を定義する方法を示しています。  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
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
