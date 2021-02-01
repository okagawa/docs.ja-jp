---
title: コピー コンストラクターを記述する方法 - C# プログラミング ガイド
description: クラスのインスタンスを受け取り、入力の値を使用して新しいインスタンスを返すコピー コンストラクターを C# で記述する方法について説明します。
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: db26b26ebcc51b57fdbe58ddaf92e5019cb69659
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899387"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>コピー コンストラクターを記述する方法 (C# プログラミング ガイド)

C# では、オブジェクトのコピー コンストラクターが提供されていませんが、独自に作成することができます。  
  
## <a name="example"></a>例  

 次の例の `Person`[クラス](../../language-reference/keywords/class.md)では、`Person` のインスタンスを引数として受け取るコピー コンストラクターが定義されています。 引数のプロパティの値は、`Person`の新しいインスタンスのプロパティに割り当てられています。 このコードには、コピーするインスタンスの `Name` プロパティと `Age` プロパティをクラスのインスタンス コンストラクターに渡す代替のコピー コンストラクターが含まれています。  
  
 [!code-csharp[CopyConstructor](snippets/how-to-write-a-copy-constructor/Program.cs)]
  
## <a name="see-also"></a>関連項目

- <xref:System.ICloneable>
- [C# プログラミング ガイド](../index.md)
- [クラスと構造体](./index.md)
- [コンストラクター](./constructors.md)
- [ファイナライザー](./destructors.md)
