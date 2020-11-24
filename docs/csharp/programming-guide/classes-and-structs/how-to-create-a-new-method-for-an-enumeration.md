---
title: 列挙型対応の新しいメソッドを作成する方法 - C# プログラミング ガイド
description: 拡張メソッドを使用して C# で列挙型に機能を追加する方法について説明します。 この例では、成績と呼ばれる列挙型に対して合格という拡張メソッドを示しています。
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 862eb86a5b0cc6b95302260874222bbc09d98132
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099413"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>列挙型対応の新しいメソッドを作成する方法 (C# プログラミング ガイド)

拡張メソッドを使用して、特定の列挙型に固有の機能を追加することができます。  
  
## <a name="example"></a>例  

 次の例では、`Grades` 列挙型は学生が授業で受け取る成績評価を表わしています。 `Passing` という名前の拡張機能メソッドが `Grades` 型に追加されていて、この型の各インスタンスが合格点を表しているかどうかを自ら "認識" できるようになっています。  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 `Extensions` クラスには動的に更新される静的変数も含まれていて、拡張メソッドの戻り値はその変数の現在の値を反映していることに注意してください。 背後では、拡張メソッドが自分が定義されている静的クラスに直接呼び出されることを、この例は示しています。  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [拡張メソッド](./extension-methods.md)
