---
title: Protobuf maps for dictionary-gRPC for WCF 開発者
description: Protobuf maps を使用して .NET で辞書型を表す方法について説明します。
ms.date: 12/15/2020
ms.openlocfilehash: d38270d4bc320cf1f758080c18843ed1d716b350
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938547"
---
# <a name="protobuf-maps-for-dictionaries"></a>Protobuf のディクショナリのマップ

メッセージ内の名前付きの値の任意のコレクションを表すことができることが重要です。 .NET では、通常、このアクティビティはディクショナリ型によって処理されます。 <xref:System.Collections.Generic.IDictionary%602>プロトコルバッファー (Protobuf) の .net 型に相当するものが `map<key_type, value_type>` 型です。 このセクションでは、Protobuf で型を宣言する方法 `map` と、生成されたコードを使用する方法について説明します。

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

生成されたコードで `map` は、フィールドは、型の読み取り専用プロパティによって表され [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] ます。 この型は、を含む標準の .NET コレクションインターフェイスを実装し <xref:System.Collections.Generic.IDictionary%602> ます。

マップフィールドは、メッセージ定義内で直接繰り返すことはできません。 ただし、次の例のように、マップを含む入れ子になったメッセージを作成し、メッセージの種類でを使用することができ `repeated` ます。

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>コードでの MapField プロパティの使用

`MapField`フィールドから生成されたプロパティ `map` は読み取り専用であり、になることはありません `null` 。 マッププロパティを設定するには、空のプロパティに対してメソッドを使用して、 `Add(IDictionary<TKey,TValue> values)` `MapField` 任意の .net ディクショナリから値をコピーします。

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a>参考資料

Protobuf の詳細については、公式の [Protobuf のドキュメント](https://developers.google.com/protocol-buffers/docs/overview)を参照してください。

[map-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/map-field-t-key-t-value-

>[!div class="step-by-step"]
>[前へ](protobuf-enums.md)
>[次へ](wcf-services-to-grpc-comparison.md)
