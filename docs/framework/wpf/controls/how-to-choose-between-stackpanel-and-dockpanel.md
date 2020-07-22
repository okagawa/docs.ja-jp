---
title: '方法: StackPanel または DockPanel を選択する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], StackPanel control compared to
- StackPanel control [WPF], DockPanel control compared to
- controls [WPF], StackPanel
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
ms.openlocfilehash: bdf4b38e67a7856136224368e86609c135e5ad6f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976442"
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a>方法: StackPanel または DockPanel を選択する
この例では、<xref:System.Windows.Controls.Panel> のコンテンツを等間隔に配置するときに、<xref:System.Windows.Controls.StackPanel> と <xref:System.Windows.Controls.DockPanel> のどちらを使用するかを選択する方法を示します。

## <a name="example"></a>例
 <xref:System.Windows.Controls.DockPanel> または <xref:System.Windows.Controls.StackPanel> を使用して子要素を等間隔に配置することはできますが、2 つのコントロールで同じ結果が生成されるとは限りません。 たとえば、子要素を配置する順序は、<xref:System.Windows.Controls.DockPanel> では子要素のサイズに影響する可能性がありますが、<xref:System.Windows.Controls.StackPanel> では影響しません。 このような異なる動作が発生するのは、<xref:System.Windows.Controls.StackPanel> では [Double.PositiveInfinity](xref:System.Double.PositiveInfinity) で等間隔の配置方向に測定されるのに対して、<xref:System.Windows.Controls.DockPanel> では使用可能なサイズのみ測定されるためです。

 次の例は、<xref:System.Windows.Controls.DockPanel> と <xref:System.Windows.Controls.StackPanel> の主な違いを示しています。

 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.DockPanel>
- [パネルの概要](panels-overview.md)
