---
title: '方法: FocusVisualStyle をコントロールに適用する'
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: b44330ee7554f953389556bd62ff49db120b5db9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459808"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>方法: FocusVisualStyle をコントロールに適用する
この例では、<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> プロパティを使用して、リソースにフォーカス表示スタイルを作成し、そのスタイルをコントロールに適用する方法を示します。  
  
## <a name="example"></a>例  
 次の例では、コントロールがユーザー インターフェイス (UI)[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] でキーボード フォーカスされている場合にのみ適用される追加のコントロール複合を作成するスタイルを定義します。 これは、<xref:System.Windows.Controls.ControlTemplate> でスタイルを定義して、<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> プロパティを設定するときに、そのスタイルをリソースとして参照することで実現します。  
  
 枠線のような外部の四角形は、四角形の領域の外側に配置されます。 特に変更がない限り、スタイルのサイズ変更では、フォーカス表示スタイルが適用される四角形コントロールの <xref:System.Windows.FrameworkElement.ActualHeight%2A> と <xref:System.Windows.FrameworkElement.ActualWidth%2A> を使用します。 この例では、<xref:System.Windows.FrameworkElement.Margin%2A> に負の値を設定して、フォーカスされたコントロールの外に枠線が少し表示されるようにします。  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> は、明示的なスタイルまたはテーマ スタイルから取得したコントロール テンプレート スタイルへの追加です。コントロールのプライマリ スタイルは、<xref:System.Windows.Controls.ControlTemplate> を使用し、そのスタイルを <xref:System.Windows.FrameworkElement.Style%2A> プロパティに設定することで作成できます。  
  
 フォーカス表示スタイルは、フォーカスできる要素ごとに異なるものを使用するのではなく、テーマまたは UI 全体で一貫したものを使用する必要があります。 詳細については、「[コントロールのフォーカスのスタイルと FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [スタイルとテンプレート](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [コントロールのフォーカスのスタイルと FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md)
