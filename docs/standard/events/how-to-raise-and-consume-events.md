---
title: '方法: イベントを発生させる/処理する'
description: .NET でイベントを発生させ、使用します。 EventHandler デリゲート、EventHandler<TEventArgs> デリゲート、カスタム デリゲートを使用する例を参照します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET], raising
- raising events
- events [.NET], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
ms.openlocfilehash: 22e62dd8e14696273923873353b1bd19d8507ab7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697455"
---
# <a name="how-to-raise-and-consume-events"></a>方法: イベントを発生させる/処理する

このトピックの例では、イベントを使用する方法を示します。 ここでは、<xref:System.EventHandler> デリゲートと <xref:System.EventHandler%601> デリゲート、およびカスタム デリゲートの例を使用して、データを持つイベントと持たないイベントを示します。  
  
 この例では、「[イベント](index.md)」で説明されている概念を使用します。  
  
## <a name="example"></a>例  

 最初の例は、データを持たないイベントを発生させて処理する方法を示しています。 この例には、`Counter` という名前のイベントを持つ、`ThresholdReached` という名前のクラスが含まれます。 このイベントは、カウンター値がしきい値と等しいか、またはそれを超えた場合に発生します。 イベントのデータが指定されていないため、<xref:System.EventHandler> デリゲートはイベントに関連付けられます。  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>例  

 次の例は、データを持つイベントを発生させて処理する方法を示しています。 <xref:System.EventHandler%601> デリゲートはイベントに関連付けられ、カスタム イベント データ オブジェクトのインスタンスが提供されます。  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>例  

 次の例は、イベントのデリゲートを宣言する方法を示しています。 デリゲートの名前は `ThresholdReachedEventHandler` です。 これはあくまでも一例です。 通常は、<xref:System.EventHandler> デリゲートまたは <xref:System.EventHandler%601> デリゲートを使用できるため、イベントのデリゲートを宣言する必要はありません。 ジェネリックを使用できないレガシ コードでクラスを使用できるようにするなど、ごくまれに、デリゲートの宣言が必要になることがあります。  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>関連項目

- [イベント](index.md)
