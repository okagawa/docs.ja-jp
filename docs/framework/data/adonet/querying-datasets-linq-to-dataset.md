---
title: DataSet のクエリ (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: bb64abcffdbbcd46dfb11b2564619c565e461436
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634782"
---
# <a name="querying-datasets-linq-to-dataset"></a>DataSet のクエリ (LINQ to DataSet)
<xref:System.Data.DataSet> オブジェクトへのデータの読み込みが完了すると、そのデータセットに対してクエリを実行できるようになります。 LINQ to DataSet でのクエリの作成は、他の LINQ (統合言語クエリ) 対応データ ソースに対して LINQ を使用する場合と似ています。 ただし、<xref:System.Data.DataSet> オブジェクトに対して LINQ クエリを使用する場合は、カスタム型の列挙型ではなく、<xref:System.Data.DataRow> オブジェクトの列挙型のクエリを実行しているということに注意してください。 つまり、LINQ クエリでは、<xref:System.Data.DataRow> クラスの任意のメンバーを使用できます。 これにより、高度で複雑なクエリを作成できます。  
  
 LINQ の他の実装と同じように、LINQ to DataSet クエリは、クエリ式の構文とメソッド ベースのクエリ構文という 2 つの異なる形式で作成できます。 クエリ式の構文またはメソッド ベースのクエリ構文を使用して、<xref:System.Data.DataSet> 内の単一テーブル、<xref:System.Data.DataSet> 内の複数テーブル、または、型指定された <xref:System.Data.DataSet> 内のテーブルを対象にクエリを実行できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [単一テーブルのクエリ](single-table-queries-linq-to-dataset.md)  
 単一テーブルのクエリを実行する方法について説明します。  
  
 [複数テーブルにまたがるクエリ](cross-table-queries-linq-to-dataset.md)  
 複数テーブルにまたがるクエリを実行する方法について説明します。  
  
 [型指定された DataSet のクエリ](querying-typed-datasets.md)  
 型指定された <xref:System.Data.DataSet> オブジェクトに対してクエリを実行する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [LINQ to DataSet の例](linq-to-dataset-examples.md)
- [DataSet へのデータの読み込み](loading-data-into-a-dataset.md)
