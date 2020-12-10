---
title: System.Text.Json でプロパティの名前と値をカスタマイズする方法
description: .NET で System.Text.Json を使用してシリアル化するときに、プロパティの名前と値をカスタマイズする方法について説明します。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: c754d41071e886bc1efcc3a30e249bf9e554ab5b
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599591"
---
# <a name="how-to-customize-property-names-and-values-with-no-locsystemtextjson"></a>System.Text.Json でプロパティの名前と値をカスタマイズする方法

既定では、プロパティ名とディクショナリ キーは、大文字と小文字の区別を含め、JSON の出力では変更されません。 列挙型の値は数値として表されます。 この記事では、次の方法について学習します。

> [!NOTE]
> [Web の既定値](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)はキャメル ケースです。

* [個々のプロパティ名をカスタマイズする](#customize-individual-property-names)
* [すべてのプロパティ名をキャメル ケースに変換する](#use-camel-case-for-all-json-property-names)
* [カスタム プロパティの名前付けポリシーを実装する](#use-a-custom-json-property-naming-policy)
* [ディクショナリ キーをキャメル ケースに変換する](#camel-case-dictionary-keys)
* [列挙型を文字列およびキャメル ケースに変換する](#enums-as-strings)

JSON プロパティの名前と値の特別な処理を必要とするその他のシナリオでは、[カスタム コンバーターを実装](system-text-json-converters-how-to.md)することができます。

## <a name="customize-individual-property-names"></a>個々のプロパティ名をカスタマイズする

個々のプロパティの名前を設定するには、[[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) 属性を使用します。

シリアル化する型と、結果として得られる JSON の例を次に示します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

この属性によって設定されるプロパティ名は:

* シリアル化と逆シリアル化の両方の方向に適用されます。
* プロパティの名前付けポリシーよりも優先されます。

## <a name="use-camel-case-for-all-json-property-names"></a>すべての JSON プロパティ名にキャメル ケースを使用する

すべての JSON プロパティ名にキャメル ケースを使用するには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> を `JsonNamingPolicy.CamelCase` に設定します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs" id="Serialize":::

シリアル化するクラスと JSON 出力の例を次に示します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

キャメル ケースのプロパティの名前付けポリシーは:

* シリアル化と逆シリアル化に適用されます。
* `[JsonPropertyName]` 属性によってオーバーライドされます。 このため、この例の JSON プロパティ名 `Wind` はキャメル ケースではありません。

## <a name="use-a-custom-json-property-naming-policy"></a>カスタム JSON プロパティの名前付けポリシーを使用する

カスタム JSON プロパティの名前付けポリシーを使用するには、次の例に示すように、<xref:System.Text.Json.JsonNamingPolicy> から派生するクラスを作成し、<xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> メソッドをオーバーライドします。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs":::

次に、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> プロパティを名前付けポリシー クラスのインスタンスに設定します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs" id="Serialize":::

シリアル化するクラスと JSON 出力の例を次に示します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

JSON プロパティの名前付けポリシーは:

* シリアル化と逆シリアル化に適用されます。
* `[JsonPropertyName]` 属性によってオーバーライドされます。 このため、この例の JSON プロパティ名 `Wind` は大文字ではありません。

## <a name="camel-case-dictionary-keys"></a>キャメル ケースのディクショナリ キー

シリアル化するオブジェクトのプロパティが `Dictionary<string,TValue>` 型である場合は、`string` キーをキャメル ケースに変換できます。 これを行うには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> を `JsonNamingPolicy.CamelCase` に設定します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs" id="Serialize":::

キーと値のペア `"ColdMinTemp", 20` および `"HotMinTemp", 40` を持つ `TemperatureRanges` という名前のディクショナリを使用してオブジェクトをシリアル化すると、次の例のような JSON 出力が生成されます。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

ディクショナリ キーに対するキャメル ケースの名前付けポリシーは、シリアル化にのみ適用されます。 ディクショナリを逆シリアル化すると、`DictionaryKeyPolicy` に `JsonNamingPolicy.CamelCase` を指定した場合でも、キーが JSON ファイルと一致します。

## <a name="enums-as-strings"></a>文字列としての列挙型

既定では、列挙型は数値としてシリアル化されます。 列挙型名を文字列としてシリアル化するには、<xref:System.Text.Json.Serialization.JsonStringEnumConverter> を使用します。

たとえば、列挙型を持つ次のクラスをシリアル化する必要があるとします。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnum":::

Summary が `Hot` の場合、既定では、シリアル化された JSON には数値 3 があります。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

次のサンプル コードでは、数値ではなく列挙型名をシリアル化し、名前をキャメル ケースに変換します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs" id="Serialize":::

結果として生成される JSON は、次の例のようになります。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

列挙型の文字列名も、次の例に示すように逆シリアル化できます。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs" id="Deserialize":::

## <a name="see-also"></a>関連項目

* [System.Text.Json の概要](system-text-json-overview.md)
* [JsonSerializerOptions をインスタンス化する](system-text-json-configure-options.md)
* [大文字と小文字を区別しない一致を有効にする](system-text-json-character-casing.md)
* [プロパティを無視する](system-text-json-ignore-properties.md)
* [無効な JSON を許可する](system-text-json-invalid-json.md)
* [オーバーフロー JSON の処理](system-text-json-handle-overflow.md)
* [循環参照の保持](system-text-json-preserve-references.md)
* [変更できない型と非パブリック アクセサー](system-text-json-immutability.md)
* [ポリモーフィックなシリアル化](system-text-json-polymorphism.md)
* [System.Text.Json API リファレンス](xref:System.Text.Json)
