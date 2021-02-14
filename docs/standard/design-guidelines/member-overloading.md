---
description: '詳細情報: メンバーのオーバーロード'
title: メンバーのオーバーロード
ms.date: 10/22/2008
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: d3a545bfec552686e55c9f713d58784497946819
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641955"
---
# <a name="member-overloading"></a>メンバーのオーバーロード

メンバーのオーバーロードとは、パラメーターの数または型は異なっているが名前は同じである同じ型の複数のメンバーを作成することです。 たとえば、以下では、`WriteLine` メソッドがオーバーロードされます。

```csharp
public static class Console {
    public void WriteLine();
    public void WriteLine(string value);
    public void WriteLine(bool value);
    ...
}
```

 パラメーターを使用できるのはメソッド、コンストラクター、およびインデックス付きプロパティだけなので、これらのメンバーのみをオーバーロードできます。

 オーバーロードは、再利用可能なライブラリの有用性、生産性、および可読性を向上させるための最も重要な手法の 1 つです。 パラメーターの数をオーバーロードすることで、より単純なバージョンのコンストラクターとメソッドを用意することが可能になります。 パラメーターの型をオーバーロードすると、型が異なる選択セットに対して同じ操作を実行するメンバーで、同じメンバー名を使用することができます。

 ✔️ 説明的なパラメーター名を使用して、短いオーバーロードによって使用される既定の設定を指示するようにしてください。

 ❌ オーバーロード内のパラメーター名を任意に変更することは避けてください。 1 つのオーバーロード内のパラメーターが別のオーバーロード内のパラメーターと同じ入力を表している場合、パラメーターの名前は同じにしてください。

 ❌ オーバーロードされたメンバーのパラメーターの順序を一貫性のないものにすることは避けてください。 同じ名前のパラメーターは、すべてのオーバーロード内で同じ位置に出現するようにしてください。

 ✔️ 最も長いオーバーロードだけを仮想にしてください (拡張性が必要な場合)。 短いオーバーロードは、長いオーバーロードを通して呼び出してください。

 ❌ `ref` または `out` 修飾子を使用してメンバーをオーバーロードしないでください。

 一部の言語では、このようなオーバーロードに対する呼び出しを解決することができません。 また、このようなオーバーロードのセマンティクスは、通常は完全に異なっているため、おそらくオーバーロードすべきではありません。代わりに 2 つの異なるメソッドを使用してください。

 ❌ セマンティクスは異なるが、同じ位置に似たような型があるパラメーターを使用してオーバーロードしないでください。

 ✔️ 省略可能な引数に対して `null` を渡すことを許可してください。

 ✔️ 既定の引数があるメンバーを定義する代わりに、メンバーのオーバーロードを使用してください。

 既定の引数は CLS 準拠ではありません。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [メンバーのデザインのガイドライン](member.md)
- [フレームワーク デザインのガイドライン](index.md)
