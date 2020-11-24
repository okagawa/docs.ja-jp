---
title: .NET で新しい文字列を作成する
description: 割り当て、クラス コンストラクター、または System.String メソッドを使用して文字列を作成する方法について学習します。これにより、.NET で複数の文字列、文字列の配列、またはオブジェクトが結合されます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
ms.openlocfilehash: a00274b7b6b7e7a54d8546f2176109688a4c4678
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824884"
---
# <a name="creating-new-strings-in-net"></a>.NET で新しい文字列を作成する

.NET は、単純な割り当てを使用した文字列の作成をサポートしています。また、多数の異なるパラメーターを使用した文字列を作成できるよう、クラス コンストラクターをオーバーロードできます。 .NET には、<xref:System.String?displayProperty=nameWithType> クラスにいくつかの文字列、文字列の配列、またはオブジェクトを組み合わせて新しい文字列オブジェクトを作成できるメソッドもいくつかあります。  
  
## <a name="creating-strings-using-assignment"></a>割り当てを使用した文字列の作成  
 新しい <xref:System.String> オブジェクトを作成する最も簡単な方法としては、単に文字列リテラルを <xref:System.String> オブジェクトに割り当てます。  
  
## <a name="creating-strings-using-a-class-constructor"></a>クラス コンストラクターを使用した文字列の作成  
 <xref:System.String> クラス コンストラクターのオーバーロードを使用すると、文字配列から文字列を作成できます。 また、指定した回数だけ特定の文字を複製することで、新しい文字列を作成することもできます。  
  
## <a name="methods-that-return-strings"></a>文字列を返すメソッド  
 次の表は、新しい文字列オブジェクトを返すいくつかの便利なメソッドを示しています。  
  
|メソッド名|使用|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|入力オブジェクトのセットから、書式設定された文字列をビルドします。|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|2 つ以上の文字列から文字列をビルドします。|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|文字列の配列を組み合わせることで、新しい文字列をビルドします。|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|既存の文字列の指定のインデックスに文字列を挿入することで、新しい文字列をビルドします。|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|文字配列内の指定の位置に、文字列内の指定の文字をコピーします。|  
  
### <a name="format"></a>形式  
 **String.Format** メソッドを使用すると、書式設定された文字列を作成し、複数のオブジェクトを表す文字列を連結できます。 このメソッドは、渡されたすべてのオブジェクトを文字列に自動的に変換します。 たとえば、アプリケーションでユーザーに対して **Int32** 値と **DateTime** 値を表示する必要がある場合、**Format** メソッドを使用して、これらの値を表す文字列を簡単に作成できます。 このメソッドで使用される書式設定規則については、[複合書式指定](composite-formatting.md)に関するセクションを参照してください。  
  
 次の例では、**Format** メソッドを使用して、整数型の変数を使用する文字列を作成します。  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 この例では、<xref:System.DateTime.Now%2A?displayProperty=nameWithType> は、現在のスレッドに関連付けられているカルチャで指定された方法で現在の日時を表示します。  
  
### <a name="concat"></a>Concat  
 **String.Concat** メソッドを使用すると、2 つ以上の既存のオブジェクトから新しい文字列オブジェクトを簡単に作成できます。 言語に依存せずに文字列を連結する方法を提供します。 このメソッドは、**System.Object** から派生したすべてのクラスを受け入れます。 次の例では、2 つの既存の文字列オブジェクトおよび区切り文字から文字列を作成します。  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Join  
 **String.Join** メソッドは、文字列の配列および区切り文字列から新しい文字列を作成します。 このメソッドは、複数の文字列を連結して、たとえばコンマで区切られたリストを作成する場合に便利です。  
  
 次の例では、スペースを使用して文字列の配列をバインドします。  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>挿入  
 **String.Insert** メソッドは、別の文字列内の指定の位置に文字列を挿入することで、新しい文字列を作成します。 このメソッドは、0 から始まるインデックスを使用します。 次の例では、`MyString` の 5 番目のインデックス位置に文字列を挿入し、この値を持つ新しい文字列を作成します。  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>CopyTo  
 **String.CopyTo** メソッドは、文字配列に文字列の部分をコピーします。 文字列の開始インデックスと、コピーする文字数の両方を指定できます。 このメソッドは、ソース インデックス、文字配列、コピー先のインデックス、およびコピーする文字数を受け取ります。 すべてのインデックスは 0 から始まります。  
  
 次の例では、**CopyTo** メソッドを使用して、文字列オブジェクトから文字配列の最初のインデックス位置に、単語 "Hello" の文字をコピーします。  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>関連項目

- [基本的な文字列操作](basic-string-operations.md)
- [複合書式指定](composite-formatting.md)
