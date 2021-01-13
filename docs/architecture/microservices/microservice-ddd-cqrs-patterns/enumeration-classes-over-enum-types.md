---
title: 列挙型ではなく列挙型クラスを使用する
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | enum のいくつかの制限を解決する方法として、代わりに Enumeration クラスを使用する方法を説明します。
ms.date: 11/25/2020
ms.openlocfilehash: a45347d7cc9c3fc6378198ca1c44ba6fecfd54f5
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899529"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a>enum 型の代わりに Enumeration クラスを使用する

[列挙型](../../../csharp/language-reference/builtin-types/enum.md) (省略形も同じ *列挙型*) は、整数型を包む薄い言語ラッパーです。 閉じた値のセットから 1 つの値を格納するときに、列挙型の使用を制限することができます。 サイズ (小、中、大) に基づく分類は良い一例です。 制御フローまたはより堅牢な抽象化のために列挙型を使用すると、[コードの臭い](https://deviq.com/antipatterns/code-smells)になることがあります。 このような用法は、列挙型の値を検査する多くの制御フロー ステートメントでは脆弱なコードにつながります。

代わりに、オブジェクト指向言語の豊富な機能をすべて使用できる列挙型クラスを作成する方法があります。

ただし、これは重要な話題ではなく、多くの場合は、好みに応じてわかりやすくするために通常の[列挙型](../../../csharp/language-reference/builtin-types/enum.md)を使用することができます。 列挙型クラスを使用するとビジネス関連の概念に対する関連性が強くなります。

## <a name="implement-an-enumeration-base-class"></a>Enumeration 基底クラスを実装する

eShopOnContainers 内の注文マイクロサービスは、次の例のように、列挙型基底クラスの実装サンプルを提供しています。

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }

    public int Id { get; private set; }

    protected Enumeration(int id, string name) => (Id, Name) = (id, name);

    public override string ToString() => Name;

    public static IEnumerable<T> GetAll<T>() where T : Enumeration =>
        typeof(T).GetFields(BindingFlags.Public |
                            BindingFlags.Static |
                            BindingFlags.DeclaredOnly)
                 .Select(f => f.GetValue(null))
                 .Cast<T>();

    public override bool Equals(object obj)
    {
        if (obj is not Enumeration otherValue)
        {
            return false;
        }

        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);

        return typeMatches && valueMatches;
    }

    public int CompareTo(object other) => Id.CompareTo(((Enumeration)other).Id);

    // Other utility methods ...
}
```

次の `CardType` : `Enumeration` クラスに関しては、このクラスを任意のエンティティまたは値オブジェクトの型として使用できます。

```csharp
public class CardType
    : Enumeration
{
    public static CardType Amex = new CardType(1, nameof(Amex));
    public static CardType Visa = new CardType(2, nameof(Visa));
    public static CardType MasterCard = new CardType(3, nameof(MasterCard));

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a>その他の技術情報

- **Jimmy Bogard。列挙型クラス** \
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- **Steve Smith。C# の列挙型の代替** \
  <https://ardalis.com/enum-alternatives-in-c>

- **Enumeration.cs。** eShopOnContainers の基底列挙型クラス \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- **CardType.cs**。 eShopOnContainers のサンプル列挙型クラス。 \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- **SmartEnum**. Ardalis - .NET で厳密に型指定されたスマートな列挙型を生成するためのクラス。 \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
>[前へ](implement-value-objects.md)
>[次へ](domain-model-layer-validations.md)
