---
title: コントロールの余白と埋め込み
description: 余白と余白のプロパティを使用して、Windows フォームコントロールに余白と埋め込みを追加する方法について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
ms.openlocfilehash: 4279f39bb4f89fbda8be472f49c8e60853abcac6
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174485"
---
# <a name="margin-and-padding-in-windows-forms-controls"></a>Windows フォーム コントロールでのマージンと埋め込み
フォーム上のコントロールを正確に配置することは、多くのアプリケーションで優先度の高い作業です。 <xref:System.Windows.Forms?displayProperty=nameWithType> 名前空間は、これを実現する多くのレイアウト機能を提供します。 最も重要な 2 つは、<xref:System.Windows.Forms.Control.Margin%2A> プロパティと <xref:System.Windows.Forms.Control.Padding%2A> プロパティです。  
  
 <xref:System.Windows.Forms.Control.Margin%2A> プロパティは、その他のコントロールで、コントロールの枠線からの指定された距離を保持するコントロールの周囲のスペースを定義します。  
  
 <xref:System.Windows.Forms.Control.Padding%2A> プロパティは、コントロールの内容 (<xref:System.Windows.Forms.Control.Text%2A> プロパティの値など) で、コントロールの枠線からの指定した距離を保持するコントロールの内部のスペースを定義します。  
  
 次の図は、コントロールの <xref:System.Windows.Forms.Control.Padding%2A> プロパティと <xref:System.Windows.Forms.Control.Margin%2A> プロパティを示しています。  
  
 ![Windows フォーム コントロールのパディングとマージン](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 Visual Studio では、この機能のデザイン時サポートがあります。 「[チュートリアル: 埋め込み、余白、AutoSize プロパティを使用した Windows フォームコントロールのレイアウト](windows-forms-controls-padding-autosize.md)」も参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
