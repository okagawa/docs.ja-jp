---
title: ListView コントロールを使用して項目を追加および削除する
description: 項目を指定してプロパティを割り当てることによって、Windows フォーム ListView コントロールで項目を追加および削除する方法について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: db374ded69bcbd93527381d75a8ff751a1c9abe6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618091"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a>方法: Windows フォーム ListView コントロールで項目を追加および削除する
項目を Windows フォームコントロールに追加するプロセスは、 <xref:System.Windows.Forms.ListView> 主に項目を指定し、その項目にプロパティを割り当てることによって構成されます。 リスト項目の追加または削除は、いつでも行うことができます。  
  
### <a name="to-add-items-programmatically"></a>プログラムによって項目を追加するには  
  
1. <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A>プロパティのメソッドを使用し <xref:System.Windows.Forms.ListView.Items%2A> ます。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a>プログラムによって項目を削除するには  
  
1. <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A>プロパティのメソッドまたはメソッドを使用し <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> <xref:System.Windows.Forms.ListView.Items%2A> ます。 メソッドは、 <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> 1 つの項目を削除します。メソッドは、 <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> リストからすべての項目を削除します。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ListView>
- [ListView コントロール](listview-control-windows-forms.md)
- [ListView コントロールの概要](listview-control-overview-windows-forms.md)
