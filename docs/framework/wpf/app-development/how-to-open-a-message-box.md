---
title: '方法: メッセージ ボックスを開く'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: bd2c4dce78e46163eb4628cb3aab829fc0173edf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123728"
---
# <a name="how-to-open-a-message-box"></a>方法: メッセージ ボックスを開く
この例では、メッセージ ボックスを開く方法を示します。  
  
## <a name="example"></a>例  
 メッセージ ボックスは、ユーザーに情報を表示するための作成済みのモーダル ダイアログ ボックスです。 メッセージ ボックスを開くには、<xref:System.Windows.MessageBox> クラスの静的 <xref:System.Windows.MessageBox.Show%2A> メソッドを呼び出します。 <xref:System.Windows.MessageBox.Show%2A> を呼び出すときに、文字列パラメーターを使用してメッセージを渡します。 <xref:System.Windows.MessageBox.Show%2A> にはいくつかのオーバーロードがあり、メッセージ ボックスの表示方法を構成できます (「<xref:System.Windows.MessageBox>」を参照)。  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>関連項目

- [MessageBox サンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)
