---
description: "詳細情報: BC32096:型が、'System.Collections.Generic.IEnumerable(Of T)' の複数のインスタンス生成を実装するため、型 '<typename>' の 'For Each' は不適切です"
title: 型が、'System.Collections.Generic.IEnumerable(Of T)' の複数のインスタンス生成を実装するため、型 '<typename>' の 'For Each' は不適切です。
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: c96bab40d4f7216f90368cf4c5526c7b4e5532f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796211"
---
# <a name="bc32096-for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a>BC32096:型が、'System.Collections.Generic.IEnumerable(Of T)' の複数のインスタンス生成を実装するため、型 '\<typename>' の 'For Each' は不適切です。

`For Each` ステートメントで、複数の <xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドを含む反復子変数を指定しています。

 反復子変数は、.NET Framework の `Collections` 名前空間のいずれかに <xref:System.Collections.IEnumerable?displayProperty=nameWithType> または <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> インターフェイスを実装する型である必要があります。 1 つのクラスで複数の構築されたジェネリック インターフェイスを、それぞれの構築に異なる型引数を使用して実装することができます。 これを行うクラスが反復子変数に使用されている場合、その変数には複数の <xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドがあります。 このような場合、Visual Basic で呼び出すメソッドを選択することはできません。

 **エラー ID:** BC32096

## <a name="to-correct-this-error"></a>このエラーを解決するには

- [DirectCast 演算子](../operators/directcast-operator.md)または [TryCast 演算子](../operators/trycast-operator.md)を使用して、反復子変数の型を、使用する <xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドを定義するインターフェイスにキャストします。

## <a name="see-also"></a>関連項目

- [For Each...Next ステートメント](../statements/for-each-next-statement.md)
- [インターフェイス](../../programming-guide/language-features/interfaces/index.md)
