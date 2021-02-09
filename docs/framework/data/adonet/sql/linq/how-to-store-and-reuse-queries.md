---
description: '詳細情報: 方法:クエリを格納および再利用する'
title: '方法: クエリを格納および再利用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a012bd79-1809-45e3-adea-0229532396cc
ms.openlocfilehash: a9c467cc9b2e39e6bd7616c6439d02c67f43d7c2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738820"
---
# <a name="how-to-store-and-reuse-queries"></a>方法: クエリを格納および再利用する

同じ構造のクエリを何回も実行するアプリケーションでは、1 回コンパイルしたクエリを、パラメーターを変えて何回も実行する方が、多くの場合にパフォーマンスを向上できます。 たとえば、特定の市に住むすべての顧客を取得するアプリケーションで、ユーザーが、対象の市を実行時にフォームで指定するとします。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、この目的で、"*コンパイル済みクエリ*" の使用がサポートされています。  
  
> [!NOTE]
> コンパイル済みクエリは、このパターンの使用法が最も一般的です。 その他にも方法は考えられます。 たとえば、デザイナーによって生成されたコードを継承した部分クラスの静的メンバーとしてコンパイル済みクエリを格納するなどです。  
  
## <a name="example"></a>例  

 スレッド境界を越えてクエリを再利用することが必要となる場合もよくあります。 その場合には、コンパイル済みクエリを静的変数に格納することは特に有効です。 次のコード例では、`Queries` クラスはコンパイル済みクエリを格納するためのクラスで、厳密に型指定された <xref:System.Data.Linq.DataContext> を表す Northwind クラスを使用することを想定しています。  
  
 [!code-csharp[DLinqQuerying#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#6)]
 [!code-vb[DLinqQuerying#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#6)]  
  
 [!code-csharp[DLinqQuerying#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#7)]
 [!code-vb[DLinqQuerying#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#7)]  
  
## <a name="example"></a>例  

 現時点では、"*匿名型*" を返すクエリを (静的変数に) 格納することはできません。型には汎用引数として指定する名前がないからです。 この問題を回避する方法を次の例に示します。結果を表すことのできる型を作成し、それを汎用引数として使用しています。  
  
 [!code-csharp[DLinqQuerying#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#8)]
 [!code-vb[DLinqQuerying#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#8)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.Linq.CompiledQuery>
- [クエリの概念](query-concepts.md)
- [データベースに対するクエリの実行](querying-the-database.md)
