---
description: '詳細情報: DataView イベントの処理'
title: DataView イベントの処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: d3e72adefa6b320d48b90d481a20644b62009cdd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652316"
---
# <a name="handling-dataview-events"></a>DataView イベントの処理

<xref:System.Data.DataView.ListChanged> の <xref:System.Data.DataView> イベントを使用して、ビューが更新されているかどうかを確認できます。 基になるテーブルの行の追加、削除、または変更や、このスキーマの列の追加または削除、親子のリレーションシップの変更など、これらの更新を行うとこのイベントが発生します。 さらに、現在表示されている行のリストが新しい並べ替え順序またはフィルターの適用により大幅に変更された場合、**ListChanged** イベントではそのことも通知されます。  
  
 **ListChanged** イベントは、<xref:System.ComponentModel> 名前空間の **ListChangedEventHandler** デリゲートを実装し、<xref:System.ComponentModel.ListChangedEventArgs> オブジェクトを入力として受け取ります。 発生した変更の内容を確認するには、**ListChangedEventArgs** オブジェクトの **ListChangedType** プロパティの <xref:System.ComponentModel.ListChangedType> 列挙値を使用します。 行の追加、削除、または移動による変更の場合、追加された行または移動された行の新しいインデックスと削除された行の古いインデックスには、**ListChangedEventArgs** オブジェクトの **NewIndex** プロパティを使用してアクセスできます。 移動された行の場合、移動前の古いインデックスにアクセスするには **ListChangedEventArgs** オブジェクトの **OldIndex** プロパティを使用します。  
  
 **DataViewManager** では、さらにテーブルが追加または削除された場合に、または基になる **DataSet** の **Relations** コレクションが変更された場合に、そのことを通知するために **ListChanged** イベントが公開されます。  
  
 **ListChanged** イベント ハンドラーを追加する方法のコード例を次に示します。  
  
```vb  
AddHandler custView.ListChanged, _  
  New System.ComponentModel.ListChangedEventHandler( _  
  AddressOf OnListChanged)  
  
Private Shared Sub OnListChanged( _  
  sender As Object, args As System.ComponentModel.ListChangedEventArgs)  
  Console.WriteLine("ListChanged:")  
  Console.WriteLine(vbTab & "    Type = " & _  
    System.Enum.GetName(args.ListChangedType.GetType(), _  
    args.ListChangedType))  
  Console.WriteLine(vbTab & "OldIndex = " & args.OldIndex)  
  Console.WriteLine(vbTab & "NewIndex = " & args.NewIndex)  
End Sub  
```  
  
```csharp  
custView.ListChanged  += new
  System.ComponentModel.ListChangedEventHandler(OnListChanged);  
  
protected static void OnListChanged(object sender,
  System.ComponentModel.ListChangedEventArgs args)  
{  
  Console.WriteLine("ListChanged:");  
  Console.WriteLine("\t    Type = " + args.ListChangedType);  
  Console.WriteLine("\tOldIndex = " + args.OldIndex);  
  Console.WriteLine("\tNewIndex = " + args.NewIndex);  
}  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [DataViews](dataviews.md)
- [ADO.NET の概要](../ado-net-overview.md)
