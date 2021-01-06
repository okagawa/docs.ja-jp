---
title: オブジェクト初期化子を使用してオブジェクトを初期化する方法 - C# プログラミング ガイド
description: コンストラクターを呼び出さずに、C# でオブジェクト初期化子を使用して、型オブジェクトを初期化する方法について説明します。 オブジェクト初期化子を使用して、匿名型を定義します。
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 0c2d38713a1fdefd922234a02e23518c0f00add5
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512783"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>オブジェクト初期化子を使用してオブジェクトを初期化する方法 (C# プログラミング ガイド)

オブジェクト初期化子を使用すると、型のコンストラクターを明示的に呼び出さずに、宣言的な方法で型オブジェクトを初期化できます。  
  
次の例は、指定したオブジェクトでオブジェクト初期化子を使用する方法を示しています。 コンパイラでは、最初にパラメーターなしのインスタンス コンストラクターにアクセスし、メンバーの初期化を処理することで、オブジェクト初期化子が処理されます。 そのため、クラスでパラメーターなしのコンストラクターが `private` として宣言されている場合、パブリック アクセスを必要とするオブジェクト初期化子は失敗します。
  
匿名型を定義する場合は、オブジェクト初期化子を使用する必要があります。 詳細については、「[クエリで要素のプロパティのサブセットを返す方法](how-to-return-subsets-of-element-properties-in-a-query.md)」を参照してください。  
  
## <a name="example"></a>例  

次の例は、オブジェクト初期化子を使用して、新しい `StudentName` 型を初期化する方法を示しています。 この例では `StudentName` 型でプロパティが設定されます。
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

オブジェクト初期化子を使用し、オブジェクトにインデクサーを設定できます。 次の例では、インデクサーを使用する `BaseballTeam` クラスを定義し、選手を取得し、さまざまなポジションに据えます。 初期化子によって、ポジションの省略形 (野球のスコアカードに使用される各ポジションの番号) に基づき、選手を割り当てることができます。

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [オブジェクト初期化子とコレクション初期化子](object-and-collection-initializers.md)
