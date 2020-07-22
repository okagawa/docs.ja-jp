---
title: '方法: 要素の Height プロパティを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: 6500af3c637092820e538d79894d600d617953bf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124287"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>方法: 要素の Height プロパティを設定する
## <a name="example"></a>例  
 この例は、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] の 4 つの高さに関連するプロパティ間のレンダリング動作の違いを視覚的に示しています。  
  
 <xref:System.Windows.FrameworkElement> クラスでは、要素の高さの特性を記述する 4 つのプロパティが公開されています。 これらの 4 つのプロパティは競合する可能性があります。その場合、優先される値は次のように決定されます。<xref:System.Windows.FrameworkElement.MinHeight%2A> 値は <xref:System.Windows.FrameworkElement.MaxHeight%2A> 値より優先され、次に <xref:System.Windows.FrameworkElement.Height%2A> 値より優先されます。 4 つ目のプロパティの <xref:System.Windows.FrameworkElement.ActualHeight%2A> は読み取り専用であり、レイアウト プロセスとの相互作用によって決定された実際の高さが報告されます。  
  
 次の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] の例では、<xref:System.Windows.Shapes.Rectangle> 要素 (`rect1`) を <xref:System.Windows.Controls.Canvas> の子として描画します。 <xref:System.Windows.FrameworkElement.MinHeight%2A>、<xref:System.Windows.FrameworkElement.MaxHeight%2A>、および <xref:System.Windows.FrameworkElement.Height%2A> のプロパティ値を表す一連の <xref:System.Windows.Controls.ListBox> 要素を使用して、<xref:System.Windows.Shapes.Rectangle> の height プロパティを変更できます。 この方法で、各プロパティの優先順位が視覚的に表示されます。  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 次のコードビハインドの例では、<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> イベントによって発生するイベントを処理します。 各ハンドラーは、<xref:System.Windows.Controls.ListBox> から入力を受け取り、値を <xref:System.Double> として解析し、指定された高さに関連するプロパティに値を適用します。 高さの値も文字列に変換され、さまざまな <xref:System.Windows.Controls.TextBlock> 要素に書き込まれます (これらの要素の定義は、選択した XAML には表示されません)。  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 サンプル全体については、[Height プロパティのサンプル](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties)を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [要素の Width プロパティを設定する](how-to-set-the-width-properties-of-an-element.md)
- [パネルの概要](panels-overview.md)
- [Height プロパティのサンプル](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties)
