---
description: '詳細情報: 数値のシーケンスの合計の計算'
title: 数値のシーケンスの合計の計算
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: c4eb066b9286335111d96d32437291da9ea2d49a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712546"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a>数値のシーケンスの合計の計算

<xref:System.Linq.Enumerable.Sum%2A> 演算子を使用すると、シーケンス内の数値の合計を計算できます。  
  
 `Sum` の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 演算子には、次の特性があります。  
  
- 標準クエリ演算子の集計演算子 `Sum` では、空のシーケンスや null のみを含むシーケンスはゼロに評価されます。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、SQL のセマンティクスは維持されます。 したがって、空のシーケンスまたは null のみを含むシーケンスについては、`Sum` 演算子は 0 ではなく null に評価します。  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] での集計には、中間結果に対する SQL の制限が適用されます。 64 ビットの結果を使って 32 ビット整数の合計値を計算することはできません。[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] による `Sum` の変換で、オーバーフローが発生する可能性があります。 これは、標準クエリ演算子の実装で、対応するメモリ内シーケンスでオーバーフローが発生しない場合でも起こる可能性があります。  
  
## <a name="example"></a>例  

 `Order` テーブルに含まれるすべての注文の運賃の合計を求める例を次に示します。  
  
 Northwind サンプル データベースに対してこのクエリを実行した場合の出力は、`64942.6900` です。  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a>例  

 すべての製品の受注単位の合計を求める例を次に示します。  
  
 Northwind サンプル データベースに対してこのクエリを実行した場合の出力は、`780` です。  
  
 `short` には `UnitsOnOrder` 型のオーバーロードがないため、short 型 (`Sum` など) をキャストする必要があります。  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a>関連項目

- [集計クエリ](aggregate-queries.md)
- [サンプル データベースのダウンロード](downloading-sample-databases.md)
