---
description: '詳細情報: 方法:コレクション初期化子によって使用される拡張メソッドを作成して追加する (Visual Basic)'
title: '方法: コレクション初期化子によって使用される Add 拡張メソッドを作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 1fbe6f438c4761ae668a6bd6a0a2c38c8efdb439
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475475"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>方法: コレクション初期化子によって使用される拡張メソッドを作成して追加する (Visual Basic)

コレクション初期化子を使用してコレクションを作成すると、`Add` メソッドのパラメーターがコレクション初期化子の値の型と一致するコレクション型の `Add` メソッドが、Visual Basic コンパイラによって検索されます。 この `Add` メソッドは、コレクションに、コレクション初期化子の値を設定するときに使用されます。  
  
 一致する `Add` メソッドが存在せず、コレクションのコードを変更できない場合は、コレクション初期化子で必要なパラメーターを取る `Add` と呼ばれる拡張メソッドを追加できます。 この操作は、通常、コレクション初期化子をジェネリック コレクションに使用するときに行う必要があります。  
  
## <a name="example"></a>例  

 次の例では、コレクション初期化子を使用して `Employee` 型のオブジェクトを追加できるように、拡張メソッドをジェネリック <xref:System.Collections.Generic.List%601> 型に追加する方法を示します。 拡張メソッドを使用すると、短縮されたコレクション初期化子構文を使用できます。  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [コレクション初期化子](index.md)
- [方法: コレクション初期化子によって使用されるコレクションを作成する](how-to-create-a-collection-used-by-a-collection-initializer.md)
