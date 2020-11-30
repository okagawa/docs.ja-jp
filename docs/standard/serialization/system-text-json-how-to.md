---
title: C# を使用して JSON をシリアル化および逆シリアル化する方法 - .NET
description: System.Text.Json 名前空間を使用して .NET 内で JSON のシリアル化と逆シリアル化を行う方法について学習します。 サンプル コードが含まれています。
ms.date: 11/05/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 1e8c46e11d3a82ca0bce29f9cb7bbc749c219198
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676726"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a>.NET 内で JSON のシリアル化と逆シリアル化 (マーシャリングとマーシャリングの解除) を行う方法

この記事では、<xref:System.Text.Json?displayProperty=fullName> 名前空間を使用して JavaScript Object Notation (JSON) のシリアル化と逆シリアル化を行う方法について示します。 `Newtonsoft.Json` から既存のコードを移植する場合は、[`System.Text.Json` に移行する方法](system-text-json-migrate-from-newtonsoft-how-to.md)に関する記事を参照してください。

指示とサンプル コードでは、ライブラリを [ASP.NET Core](/aspnet/core/) などのフレームワーク経由ではなく直接使用します。

シリアル化のサンプル コードの大部分では、JSON を "整形" するために <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> を `true` に設定します (人間が読みやすいようにインデントと空白文字が使用されます)。 実稼働環境で使用する場合、通常、この設定には既定値の `false` をそのまま使用します。

コード例では、次のクラスとそのバリアントを参照しています。

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a>名前空間

<xref:System.Text.Json> 名前空間には、すべてのエントリ ポイントと主要な型が含まれています。 <xref:System.Text.Json.Serialization> 名前空間には、シリアル化と逆シリアル化に固有の高度なシナリオとカスタマイズのための属性と API が含まれています。 この記事に示されているコード例では、次のいずれかまたは両方の名前空間に `using` ディレクティブが必要です。

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<xref:System.Runtime.Serialization> 名前空間の属性は、`System.Text.Json` ではサポートされていません。

## <a name="how-to-write-net-objects-to-json-serialize"></a>.NET オブジェクトを JSON に書き込む方法 (シリアル化)

JSON を文字列またはファイルに書き込むには、<xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> メソッドを呼び出します。

次の例では、JSON を文字列として作成します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

次の例では、同期コードを使用して JSON ファイルを作成します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

次の例では、非同期コードを使用して JSON ファイルを作成します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

前の例では、シリアル化する型に型の推定を使用しています。 `Serialize()` のオーバーロードでは、ジェネリック型パラメーターを受け取ります。

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a>シリアル化の例

コレクション型のプロパティとユーザー定義型を含むクラスの例を次に示します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

> [!TIP]
> "POCO" は、[Plain Old CLR Object (単純な従来の CLR オブジェクト)](https://en.wikipedia.org/wiki/Plain_old_CLR_object) を表します。 POCO は、継承や属性からなど、フレームワーク固有の型に依存しない .NET 型です。

前の型のインスタンスをシリアル化した場合の JSON 出力は、次の例のようになります。 JSON 出力は既定で縮小されます。

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

次の例では、同じ JSON ですが、書式設定されているもの (空白とインデントで整形されています) を示しています。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": 20,
      "Low": -10
    },
    "Hot": {
      "High": 60,
      "Low": 20
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

### <a name="serialize-to-utf-8"></a>UTF-8 にシリアル化する

UTF-8 にシリアル化するには、<xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> メソッドを呼び出します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<xref:System.Text.Json.Utf8JsonWriter> を受け取る <xref:System.Text.Json.JsonSerializer.Serialize%2A> オーバーロードも使用できます。

UTF-8 へのシリアル化は、文字列ベースのメソッドを使用するよりも約 5-10% 高速です。 違いは、バイト (UTF-8) を文字列 (UTF-16) に変換する必要がないことから生じます。

## <a name="serialization-behavior"></a>シリアル化の動作

::: zone pivot="dotnet-5-0"

* 既定では、すべてのパブリック プロパティがシリアル化されます。 [無視するプロパティを指定する](#ignore-properties)ことができます。
* [既定のエンコーダー](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)では、ASCII 以外の文字、ASCII 範囲内の HTML に影響する文字、および [RFC 8259 JSON 仕様](https://tools.ietf.org/html/rfc8259#section-7)に従ってエスケープする必要のある文字がエスケープされます。
* 既定では、JSON は縮小されます。 [JSON を整形](#serialize-to-formatted-json)することができます。
* 既定では、JSON 名の大文字と小文字の区別は .NET 名と一致します。 [JSON 名の大文字と小文字の区別をカスタマイズ](#customize-json-names-and-values)することができます。
* 既定では、循環参照が検出され、例外がスローされます。 [参照を保持し、循環参照を処理する](#preserve-references-and-handle-circular-references)ことができます。
* 既定では、[フィールド](../../csharp/programming-guide/classes-and-structs/fields.md)は無視されます。 [フィールドを含める](#include-fields)ことができます。

ASP.NET Core アプリで System.Text.Json を間接的に使用する場合、一部の既定の動作が異なります。 詳細については、「[JsonSerializerOptions の Web の規定値](#web-defaults-for-jsonserializeroptions)」を参照してください。
::: zone-end

::: zone pivot="dotnet-core-3-1"

* 既定では、すべてのパブリック プロパティがシリアル化されます。 [無視するプロパティを指定する](#ignore-properties)ことができます。
* [既定のエンコーダー](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)では、ASCII 以外の文字、ASCII 範囲内の HTML に影響する文字、および [RFC 8259 JSON 仕様](https://tools.ietf.org/html/rfc8259#section-7)に従ってエスケープする必要のある文字がエスケープされます。
* 既定では、JSON は縮小されます。 [JSON を整形](#serialize-to-formatted-json)することができます。
* 既定では、JSON 名の大文字と小文字の区別は .NET 名と一致します。 [JSON 名の大文字と小文字の区別をカスタマイズ](#customize-json-names-and-values)することができます。
* 循環参照が検出され、例外がスローされます。
* [フィールド](../../csharp/programming-guide/classes-and-structs/fields.md)は無視されます。
::: zone-end

サポートされる型には次のようなものがあります。
::: zone pivot="dotnet-5-0"

* 数値型、文字列、ブール値など、JavaScript プリミティブにマップされる .NET プリミティブ。
* ユーザー定義の[単純な従来の CLR オブジェクト (POCO)](https://en.wikipedia.org/wiki/Plain_old_CLR_object)。
* 1 次元配列とジャグ配列 (`T[][]`)。
* 次の名前空間のコレクションとディクショナリ。
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* 数値型、文字列、ブール値など、JavaScript プリミティブにマップされる .NET プリミティブ。
* ユーザー定義の[単純な従来の CLR オブジェクト (POCO)](https://en.wikipedia.org/wiki/Plain_old_CLR_object)。
* 1 次元配列とジャグ配列 (`ArrayName[][]`)。
* `Dictionary<string,TValue>`。`TValue` は `object`、`JsonElement`、または POCO です。
* 次の名前空間からのコレクション。
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

[カスタム コンバーターを実装](system-text-json-converters-how-to.md)して、追加の型を処理したり、組み込みコンバーターではサポートされていない機能を提供したりすることができます。

## <a name="how-to-read-json-into-net-objects-deserialize"></a>JSON を .NET オブジェクトに読み取る方法 (逆シリアル化)

文字列またはファイルから逆シリアル化するには、<xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> メソッドを呼び出します。

次の例では、文字列から JSON を読み取り、前に[シリアル化の例](#serialization-example)で示した `WeatherForecastWithPOCOs` クラスのインスタンスを作成します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

同期コードを使用してファイルから逆シリアル化するには、次の例に示すように、ファイルを文字列に読み取ります。

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

非同期コードを使用してファイルから逆シリアル化するには、<xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> メソッドを呼び出します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a>UTF-8 からの逆シリアル化

UTF-8 から逆シリアル化するには、次の例に示すように、`Utf8JsonReader` または `ReadOnlySpan<byte>` を受け取る <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> オーバーロードを呼び出します。 この例では、JSON が jsonUtf8Bytes という名前のバイト配列内にあることを想定しています。

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a>逆シリアル化の動作

JSON を逆シリアル化する場合、次の動作が適用されます。

::: zone pivot="dotnet-5-0"

* 既定では、プロパティ名の照合では大文字と小文字が区別されます。 [大文字と小文字を区別しないことを指定](#case-insensitive-property-matching)できます。
* JSON に読み取り専用プロパティの値が含まれている場合、その値は無視され、例外はスローされません。
* 非パブリック コンストラクターはシリアライザーにより無視されます。
* 不変オブジェクトまたは読み取り専用プロパティへの逆シリアル化はサポートされています。 「[不変の型とレコード](#immutable-types-and-records)」を参照してください。
* 既定では、列挙型は数値としてサポートされています。 [列挙型名を文字列としてシリアル化](#enums-as-strings)することができます。
* 既定では、フィールドは無視されます。 [フィールドを含める](#include-fields)ことができます。
* 既定では、JSON にコメントまたは末尾のコンマがあると例外がスローされます。 [コメントと末尾のコンマを許可](#allow-comments-and-trailing-commas)することができます。
* [既定の最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)は 64 です。

ASP.NET Core アプリで System.Text.Json を間接的に使用する場合、一部の既定の動作が異なります。 詳細については、「[JsonSerializerOptions の Web の規定値](#web-defaults-for-jsonserializeroptions)」を参照してください。
::: zone-end

::: zone pivot="dotnet-core-3-1"

* 既定では、プロパティ名の照合では大文字と小文字が区別されます。 [大文字と小文字を区別しないことを指定](#case-insensitive-property-matching)できます。 ASP.NET Core アプリの場合、[既定では大文字と小文字を区別しないことが指定](#web-defaults-for-jsonserializeroptions)されます。
* JSON に読み取り専用プロパティの値が含まれている場合、その値は無視され、例外はスローされません。
* 逆シリアル化には、パラメーターなしのコンストラクター (public、internal、private のいずれか) が使用されます。
* 不変オブジェクトまたは読み取り専用プロパティへの逆シリアル化はサポートされていません。
* 既定では、列挙型は数値としてサポートされています。 [列挙型名を文字列としてシリアル化](#enums-as-strings)することができます。
* フィールドはサポートされません。
* 既定では、JSON にコメントまたは末尾のコンマがあると例外がスローされます。 [コメントと末尾のコンマを許可](#allow-comments-and-trailing-commas)することができます。
* [既定の最大深度](xref:System.Text.Json.JsonReaderOptions.MaxDepth)は 64 です。

ASP.NET Core アプリで System.Text.Json を間接的に使用する場合、一部の既定の動作が異なります。 詳細については、「[JsonSerializerOptions の Web の規定値](#web-defaults-for-jsonserializeroptions)」を参照してください。
::: zone-end

[カスタム コンバーターを実装](system-text-json-converters-how-to.md)して、組み込みコンバーターではサポートされていない機能を提供できます。

## <a name="serialize-to-formatted-json"></a>書式設定された JSON へのシリアル化

JSON 出力を整形するには、<xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> を `true` に設定します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

シリアル化され、整形された JSON 出力の型の例を次に示します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="include-fields"></a>フィールドを含める

::: zone pivot="dotnet-5-0"
次の例で示されているように、シリアル化または逆シリアル化のときにフィールドを含めるには、<xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> グローバル設定または [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) 属性を使用します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="15,17,19,31":::

読み取り専用フィールドを無視するには、<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> グローバル設定を使用します。
::: zone-end

::: zone pivot="dotnet-core-3-1"
.NET Core 3.1 では、System.Text.Json メソッドはサポートされていません。 この機能は、[カスタム コンバーター](system-text-json-converters-how-to.md)で提供できます。
::: zone-end

## <a name="customize-json-names-and-values"></a>JSON の名前と値をカスタマイズする

既定では、プロパティ名とディクショナリ キーは、大文字と小文字の区別を含め、JSON の出力では変更されません。 列挙型の値は数値として表されます。 このセクションでは、次の方法について説明します。

* [個々のプロパティ名をカスタマイズする](#customize-individual-property-names)
* [すべてのプロパティ名をキャメル ケースに変換する](#use-camel-case-for-all-json-property-names)
* [カスタム プロパティの名前付けポリシーを実装する](#use-a-custom-json-property-naming-policy)
* [ディクショナリ キーをキャメル ケースに変換する](#camel-case-dictionary-keys)
* [列挙型を文字列およびキャメル ケースに変換する](#enums-as-strings)

JSON プロパティの名前と値の特別な処理を必要とするその他のシナリオでは、[カスタム コンバーターを実装](system-text-json-converters-how-to.md)することができます。

### <a name="customize-individual-property-names"></a>個々のプロパティ名をカスタマイズする

個々のプロパティの名前を設定するには、[[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) 属性を使用します。

シリアル化する型と、結果として得られる JSON の例を次に示します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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

### <a name="use-camel-case-for-all-json-property-names"></a>すべての JSON プロパティ名にキャメル ケースを使用する

すべての JSON プロパティ名にキャメル ケースを使用するには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> を `JsonNamingPolicy.CamelCase` に設定します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

シリアル化するクラスと JSON 出力の例を次に示します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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

### <a name="use-a-custom-json-property-naming-policy"></a>カスタム JSON プロパティの名前付けポリシーを使用する

カスタム JSON プロパティの名前付けポリシーを使用するには、次の例に示すように、<xref:System.Text.Json.JsonNamingPolicy> から派生するクラスを作成し、<xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> メソッドをオーバーライドします。

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

次に、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> プロパティを名前付けポリシー クラスのインスタンスに設定します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

シリアル化するクラスと JSON 出力の例を次に示します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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

### <a name="camel-case-dictionary-keys"></a>キャメル ケースのディクショナリ キー

シリアル化するオブジェクトのプロパティが `Dictionary<string,TValue>` 型である場合は、`string` キーをキャメル ケースに変換できます。 これを行うには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> を `JsonNamingPolicy.CamelCase` に設定します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

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

### <a name="enums-as-strings"></a>文字列としての列挙型

既定では、列挙型は数値としてシリアル化されます。 列挙型名を文字列としてシリアル化するには、<xref:System.Text.Json.Serialization.JsonStringEnumConverter> を使用します。

たとえば、列挙型を持つ次のクラスをシリアル化する必要があるとします。

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

Summary が `Hot` の場合、既定では、シリアル化された JSON には数値 3 があります。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

次のサンプル コードでは、数値ではなく列挙型名をシリアル化し、名前をキャメル ケースに変換します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

結果として生成される JSON は、次の例のようになります。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

列挙型の文字列名も、次の例に示すように逆シリアル化できます。

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="ignore-properties"></a>プロパティを無視する

既定では、すべてのパブリック プロパティがシリアル化されます。 その一部が JSON 出力に出現しないようにするには、いくつかのオプションがあります。 このセクションでは、以下のものを無視する方法について説明します。

::: zone pivot="dotnet-5-0"

* [個々のプロパティ](#ignore-individual-properties)
* [すべての読み取り専用プロパティ](#ignore-all-read-only-properties)
* [すべての null 値プロパティ](#ignore-all-null-value-properties)
* [すべての既定値のプロパティ](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [個々のプロパティ](#ignore-individual-properties)
* [すべての読み取り専用プロパティ](#ignore-all-read-only-properties)
* [すべての null 値プロパティ](#ignore-all-null-value-properties)
::: zone-end

### <a name="ignore-individual-properties"></a>個々のプロパティを無視する

個々のプロパティを無視するには、[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 属性を使用します。

シリアル化する型と JSON 出力の例を次に示します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 属性の `Condition` プロパティを設定することによって、条件付き除外を指定できます。 <xref:System.Text.Json.Serialization.JsonIgnoreCondition> 列挙型には、次のオプションがあります。

* `Always` - プロパティを常に無視します。 `Condition` を指定しないと、このオプションが想定されます。
* `Never` - グローバル設定 `DefaultIgnoreCondition`、`IgnoreReadOnlyProperties`、`IgnoreReadOnlyFields` に関係なく、プロパティは常にシリアル化および逆シリアル化されます。
* `WhenWritingDefault` - プロパティは、参照型 `null` または値型 `default` の場合、シリアル化で無視されます。
* `WhenWritingNull` - プロパティは、参照型 `null` の場合、シリアル化で無視されます。

次の例では、[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 属性の `Condition` プロパティの使用方法を示します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

### <a name="ignore-all-read-only-properties"></a>すべての読み取り専用プロパティを無視する

パブリック ゲッターが含まれていてもパブリック セッターがない場合、プロパティは読み取り専用です。 シリアル化のときにすべての読み取り専用プロパティを無視するには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> を `true` に設定します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

シリアル化する型と JSON 出力の例を次に示します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

このオプションは、シリアル化にのみ適用されます。 逆シリアル化中、既定では読み取り専用プロパティが無視されます。

::: zone pivot="dotnet-5-0"
このオプションは、プロパティにのみ適用されます。 [フィールドをシリアル化する](#include-fields)ときに読み取り専用フィールドを無視するには、<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> グローバル設定を使用します。
::: zone-end

### <a name="ignore-all-null-value-properties"></a>すべての null 値プロパティを無視する

::: zone pivot="dotnet-5-0"
すべての null 値プロパティを無視するには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> プロパティを <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull> に設定します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
シリアル化のときにすべての null 値プロパティを無視するには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> プロパティを `true` に設定します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

シリアル化するオブジェクトと JSON 出力の例を次に示します。

|プロパティ |値  |
|---------|---------|
| Date    | 8/1/2019 12:00:00 AM -07:00|
| TemperatureCelsius| 25 |
| まとめ| null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

::: zone-end

### <a name="ignore-all-default-value-properties"></a>既定値のプロパティをすべて無視する

::: zone pivot="dotnet-5-0"
値型プロパティで既定値がシリアル化されないようにするには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> プロパティを <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> に設定します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

`WhenWritingDefault` を設定すると、null 値参照型プロパティもシリアル化されなくなります。

::: zone pivot="dotnet-core-3-1"
.NET Core 3.1 の System.Text.Json で、値型の既定値のプロパティがシリアル化されないようにするための組み込みの方法はありません。
::: zone-end

## <a name="customize-character-encoding"></a>文字エンコードをカスタマイズする

既定では、シリアライザーでは ASCII 以外のすべての文字がエスケープされます。  つまり、`\uxxxx` に置き換えられます。`xxxx` は文字の Unicode コードです。  たとえば、`Summary` プロパティがキリル文字の жарко に設定されている場合、`WeatherForecast` オブジェクトは次の例に示すようにシリアル化されます。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>言語文字セットのシリアル化

1 つ以上の言語の文字セットをエスケープせずにシリアル化するには、次の例に示すように、<xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> のインスタンスを作成するときに [Unicode 範囲](xref:System.Text.Unicode.UnicodeRanges)を指定します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

このコードでは、キリル文字やギリシャ文字はエスケープされません。 `Summary` プロパティがキリル文字の жарко に設定されている場合、`WeatherForecast` オブジェクトは次の例に示すようにシリアル化されます。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

すべての言語セットをエスケープせずにシリアル化するには、<xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> を使用します。

### <a name="serialize-specific-characters"></a>特定の文字のシリアル化

別の方法として、エスケープせずに許可する個々の文字を指定することもできます。 次の例では、жарко の最初の 2 文字のみをシリアル化します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

上記のコードによって生成される JSON の例を次に示します。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>すべての文字のシリアル化

エスケープを最小化するには、次の例に示すように、<xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> を使用できます。

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> 既定のエンコーダーと比較して、`UnsafeRelaxedJsonEscaping` エンコーダーは、文字をエスケープせずにそのまま渡すことについて、より寛容です。
>
> * `<`、`>`、`&`、`'` など、HTML に影響する文字はエスケープされません。
> * クライアントとサーバーが "*文字セット*" について合意していない場合の結果など、XSS または情報漏えい攻撃に対する追加の多層防御は提供されません。
>
> 安全でないエンコーダーは、クライアントによって結果のペイロードが UTF-8 でエンコードされた JSON として解釈されることがわかっている場合にのみ使用してください。 たとえば、サーバーが応答ヘッダー `Content-Type: application/json; charset=utf-8` を送信している場合は使用できます。 未加工の `UnsafeRelaxedJsonEscaping` 出力が HTML ページまたは `<script>` 要素に決して出力されないようにしてください。

## <a name="serialize-properties-of-derived-classes"></a>派生クラスのプロパティのシリアル化

ポリモーフィックな型階層のシリアル化はサポートされていません。 たとえば、プロパティがインターフェイスまたは抽象クラスとして定義されている場合は、ランタイム型に追加のプロパティがある場合でも、インターフェイスまたは抽象クラスに定義されたプロパティのみがシリアル化されます。 この動作の例外については、このセクションで説明します。

たとえば、`WeatherForecast` クラスと派生クラス `WeatherForecastDerived` があるとします。

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

また、コンパイル時の `Serialize` メソッドの型引数が `WeatherForecast` であるとします。

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

このシナリオでは、`weatherForecast` オブジェクトが実際には `WeatherForecastDerived` オブジェクトであっても、`WindSpeed` プロパティはシリアル化されません。 基本クラスのプロパティのみがシリアル化されます。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

この動作は、ランタイムによって作成される派生型内でデータが誤って公開されるのを防ぐためのものです。

前の例で派生型のプロパティをシリアル化するには、次のいずれかのアプローチを使用します。

* 実行時に型を指定できるようにする <xref:System.Text.Json.JsonSerializer.Serialize%2A> のオーバーロードを呼び出します。

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* オブジェクトを `object` としてシリアル化するように宣言します。

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

前の例のシナリオでは、どちらのアプローチでも、`WindSpeed` プロパティが JSON 出力に含まれるようになります。

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> これらのアプローチでは、シリアル化するルート オブジェクトに対してのみポリモーフィックなシリアル化が提供され、そのルート オブジェクトのプロパティに対しては提供されません。

`object` 型として定義すると、下位レベルのオブジェクトのポリモーフィックなシリアル化を取得できます。 たとえば、`WeatherForecast` クラスに、`WeatherForecast` または `object` 型として定義できる `PreviousForecast` という名前のプロパティがあるとします。

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

`PreviousForecast` プロパティに `WeatherForecastDerived` のインスタンスが含まれる場合:

* `WeatherForecastWithPrevious` のシリアル化からの JSON 出力には `WindSpeed` が **含まれていません**。
* `WeatherForecastWithPreviousAsObject` のシリアル化からの JSON 出力には `WindSpeed` が **含まれています**。

ルート オブジェクトは派生型である可能性があるものではないため、`WeatherForecastWithPreviousAsObject` をシリアル化するために `Serialize<object>` または `GetType` を呼び出す必要はありません。 次のコード例では `Serialize<object>` または `GetType` は呼び出されません。

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

上記のコードでは、`WeatherForecastWithPreviousAsObject` が正しくシリアル化されます。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "PreviousForecast": {
    "WindSpeed": 35,
    "Date": "2019-08-01T00:00:00-07:00",
    "TemperatureCelsius": 25,
    "Summary": "Hot"
  }
}
```

`object` と同じプロパティ定義のアプローチがインターフェイスで機能します。 次のインターフェイスと実装があり、実装インスタンスを含むプロパティを使用してクラスをシリアル化するとします。

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

`Forecasts` のインスタンスをシリアル化する場合、`Tuesday` は `object` として定義されているので、`Tuesday` にのみ `WindSpeed` プロパティが表示されます。

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

次の例は、前のコードから生成された JSON を示しています。

```json
{
  "Monday": {
    "Date": "2020-01-06T00:00:00-08:00",
    "TemperatureCelsius": 10,
    "Summary": "Cool"
  },
  "Tuesday": {
    "Date": "2020-01-07T00:00:00-08:00",
    "TemperatureCelsius": 11,
    "Summary": "Rainy",
    "WindSpeed": 10
  }
}
```

ポリモーフィック **シリアル化** の詳細、および **逆シリアル化** の詳細については、「[Newtonsoft.Json から System.Text.Json に移行する方法](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization)」を参照してください。

## <a name="allow-comments-and-trailing-commas"></a>コメントと末尾のコンマを許可する

既定では、JSON 内でコメントと末尾のコンマは使用できません。 JSON 内でコメントを許可するには、<xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> プロパティを `JsonCommentHandling.Skip` に設定します。
また、末尾のコンマを許可するには、<xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> プロパティを `true` に設定します。 両方を許可する方法を次の例に示します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

次に、コメントと末尾のコンマを含む JSON の例を示します。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a>大文字と小文字を区別しないプロパティ照合

既定では、逆シリアル化では JSON とターゲット オブジェクトのプロパティとの間で大文字と小文字を区別したプロパティ名の一致が検索されます。 この動作を変更するには、<xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> を `true` に設定します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

キャメル ケースのプロパティ名を持つ JSON の例を次に示します。 これはパスカル ケースのプロパティ名を持つ次の型に逆シリアル化できます。

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a>オーバーフロー JSON の処理

逆シリアル化中に、ターゲット型のプロパティで表されないデータを JSON 内で受け取ることがあります。 たとえば、ターゲット型が次のようになっているとします。

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

逆シリアル化される JSON は次のとおりです。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

表示されている JSON を示されている型に逆シリアル化すると、`DatesAvailable` と `SummaryWords` のプロパティは行き先がなくなり、失われます。 これらのプロパティのような余分なデータをキャプチャするには、[[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) 属性を `Dictionary<string,object>` 型または `Dictionary<string,JsonElement>` 型のプロパティに適用します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

前に示した JSON をこのサンプル型に逆シリアル化すると、余分なデータが `ExtensionData` プロパティのキーと値のペアになります。

|プロパティ |値  |メモ  |
|---------|---------|---------|
| Date    | 8/1/2019 12:00:00 AM -07:00||
| TemperatureCelsius| 0 | 大文字と小文字の区別が一致しないため (JSON では `temperatureCelsius`)、プロパティは設定されません。 |
| まとめ | ホット ||
| ExtensionData | temperatureCelsius:25 |大文字と小文字の区別が一致しなかったため、この JSON プロパティは余分で、ディクショナリ内のキーと値のペアになります。|
|| DatesAvailable:<br>  8/1/2019 12:00:00 AM -07:00<br>8/2/2019 12:00:00 AM -07:00 |JSON からの余分なプロパティは、値オブジェクトとしての配列を持つキーと値のペアになります。|
| |SummaryWords:<br>Cool<br>強風<br>Humid |JSON からの余分なプロパティは、値オブジェクトとしての配列を持つキーと値のペアになります。|

ターゲット オブジェクトがシリアル化されると、拡張データのキーと値のペアは、受信 JSON 内にあった場合と同様に JSON プロパティになります。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 0,
  "Summary": "Hot",
  "temperatureCelsius": 25,
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

JSON には `ExtensionData` プロパティ名が表示されないことに注意してください。 この動作により、JSON は、逆シリアル化されない余分なデータを失うことなく、ラウンド トリップを行うことができます。

## <a name="preserve-references-and-handle-circular-references"></a>参照を保持し、循環参照を処理する

::: zone pivot="dotnet-5-0"

参照を保持し、循環参照を処理するには、<xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> を <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> に設定します。 これを設定すると、次のような動作になります。

* シリアル化のとき:

  複合型を書き込むとき、シリアライザーによってメタデータのプロパティ (`$id`、`$values`、`$ref`) も書き込まれます。

* 逆シリアル化のとき:

  メタデータが想定され (必須ではありません)、逆シリアライザーによってその理解が試みられます。

次のコードでは、`Preserve` 設定の使用方法を示します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

この機能を使用して、値型または不変型を保持することはできません。 逆シリアル化のとき、不変型のインスタンスは、ペイロード全体が読み取られた後で作成されます。 そのため、同じインスタンスへの参照が JSON ペイロード内に含まれている場合、それを逆シリアル化することはできません。

値型、不変型、配列の場合、参照メタデータはシリアル化されません。 逆シリアル化では、`$ref` または `$id` が検出されると例外がスローされます。 ただし、Newtonsoft.Json を使用してシリアル化されたペイロードを逆シリアル化できるようにするため、`$id` (および、コレクションの場合は `$values`) は値型で無視されます。  Newtonsoft.Json の場合は、そのような型のメタデータがシリアル化されます。

オブジェクトが等しいかどうかを判断するために System.Text.Json によって使用される <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> では、2 つのオブジェクト インスタンスを比較するときに、値の等価性 (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType>) ではなく参照の等価性 (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) が使用されます。

参照がシリアル化および逆シリアル化される方法の詳細については、<xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> に関するページを参照してください。

シリアル化および逆シリアル化で参照を維持するための動作は、<xref:System.Text.Json.Serialization.ReferenceResolver> クラスによって定義されます。 カスタム動作を指定するには、派生クラスを作成します。 例については、[GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs) に関するページを参照してください。

::: zone-end

::: zone pivot="dotnet-core-3-1"
.NET Core 3.1 の System.Text.Json でサポートされているのは値によるシリアル化のみであり、循環参照の場合は例外がスローされます。
::: zone-end

## <a name="allow-or-write-numbers-in-quotes"></a>引用符で囲まれた数値を許可または記述する

::: zone pivot="dotnet-5-0"

シリアライザーの中には、数値が JSON 文字列としてエンコードされる (引用符で囲まれる) ものがあります。 たとえば、`{"DegreesCelsius":23}` ではなく `{"DegreesCelsius":"23"}` になります。 引用符で囲まれた数値をシリアル化したり、引用符で囲まれた数値を入力オブジェクト グラフ全体で受け付けるには、次の例で示されているように、<xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> を設定します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-28":::

ASP.NET Core を通じて間接的に System.Text.Json を使用すると、ASP.NET Core により [Web の既定のオプション](xref:System.Text.Json.JsonSerializerDefaults.Web)が指定されるため、逆シリアル化のときに引用符で囲まれた数値を使用できます。

特定のプロパティ、フィールド、または型について引用符で囲まれた数値を許可または記述するには、[[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) 属性を使用します。
::: zone-end

::: zone pivot="dotnet-core-3-1"
.NET Core 3.1 の System.Text.Json では、引用符で囲まれた数値のシリアル化または逆シリアル化はサポートされていません。 詳細については、「[引用符で囲まれた数値を許可または記述する](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes)」を参照してください。
::: zone-end

## <a name="immutable-types-and-records"></a>不変の型とレコード

::: zone pivot="dotnet-5-0"
System.Text.Json ではパラメーター化されたコンストラクターを使用できるので、不変のクラスまたは構造体を逆シリアル化できます。 クラスの場合、パラメーター化されたコンストラクターしかない場合は、そのコンストラクターが使用されます。 構造体または複数のコンストラクターを持つクラスの場合は、[[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) 属性を適用することにより、使用するコンストラクターを指定します。 その属性を使用しないと、パラメーターなしのパブリック コンストラクターが存在する場合は常にそれが使用されます。 その属性は、パブリック コンストラクターでのみ使用できます。 次の例では、`[JsonConstructor]` 属性が使用されています。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

次の例で示されているように、C# 9 のレコードもサポートされています。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

すべてのプロパティ セッターが非パブリックであるために不変の型の場合は、[パブリックでないプロパティ アクセサー](#non-public-property-accessors)に関する次のセクションを参照してください。
::: zone-end

::: zone pivot="dotnet-core-3-1"
`JsonConstructorAttribute` と C# 9 のレコードのサポートは、.NET Core 3.1 では使用できません。
::: zone-end

## <a name="non-public-property-accessors"></a>パブリックでないプロパティ アクセサー

::: zone pivot="dotnet-5-0"
パブリックでないプロパティ アクセサーを使用できるようにするには、次の例で示されているように、[[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) 属性を使用します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
パブリックでないプロパティ アクセサーは、.NET Core 3.1 ではサポートされていません。 詳細については、[Newtonsoft.Json からの移行の記事](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters)を参照してください。
::: zone-end

## <a name="copy-jsonserializeroptions"></a>JsonSerializerOptions をコピーする

::: zone pivot="dotnet-5-0"
次の例で示されているように、既存のインスタンスと同じオプションを使用して新しいインスタンスを作成できる [JsonSerializerOptions コンストラクター](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions))があります。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
既存のインスタンスを受け取る `JsonSerializerOptions` コンストラクターは、.NET Core 3.1 では使用できません。
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a>JsonSerializerOptions の Web の既定値

::: zone pivot="dotnet-5-0"
Web アプリ用に異なる既定値があるオプションは次のとおりです。

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

次の例で示されているように、ASP.NET Core によって Web アプリ用に使用される既定のオプションで新しいインスタンスを作成できる [JsonSerializerOptions コンストラクター](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true)があります。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
Web アプリ用に異なる既定値があるオプションは次のとおりです。

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

既定値のセットを指定する `JsonSerializerOptions` コンストラクターは、.NET Core 3.1 では使用できません。
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a>HttpClient と HttpContent の拡張メソッド

::: zone pivot="dotnet-5-0"

ネットワークからの JSON ペイロードのシリアル化と逆シリアル化は、一般的な操作です。 [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) および [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) の拡張メソッドを使用すると、これらの操作を 1 行のコードで実行できます。 これらの拡張メソッドにおいては、[JsonSerializerOptions の Web の既定値](#web-defaults-for-jsonserializeroptions)が使用されます。

次の例では、<xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> と <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> の使用方法を示します。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="23,30":::

[HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) には System.Text.Json 用の拡張メソッドもあります。
::: zone-end

::: zone pivot="dotnet-core-3-1"
`HttpClient` および `HttpContent` の拡張メソッドは、.NET Core 3.1 の System.Text.Json では使用できません。
::: zone-end

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader、Utf8JsonWriter、JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> は、UTF-8 でエンコードされた JSON テキスト用の、ハイパフォーマンス、低割り当て、順方向専用のリーダーです。`ReadOnlySpan<byte>` または `ReadOnlySequence<byte>` から読み取られます。 `Utf8JsonReader` は低レベルの型であり、カスタム パーサーとデシリアライザーを構築するために使用できます。 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> メソッドでは、内部で `Utf8JsonReader` が使用されます。

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> は、`String`、`Int32`、`DateTime` のような一般的な .NET 型から UTF-8 でエンコードされた JSON テキストを書き込むための、ハイパフォーマンスな方法です。 ライターは低レベルの型であり、カスタム シリアライザーを構築するために使用できます。 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> メソッドでは、内部で `Utf8JsonWriter` が使用されます。

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> では、`Utf8JsonReader` を使用して、読み取り専用のドキュメント オブジェクト モデル (DOM) を構築する機能が提供されます。 DOM では、JSON ペイロード内のデータへのランダム アクセスが提供されます。 ペイロードを構成する JSON 要素には、<xref:System.Text.Json.JsonElement> 型を使用してアクセスできます。 `JsonElement` 型では、配列とオブジェクト列挙子と共に、JSON テキストを一般的な .NET 型に変換する API が提供されます。 `JsonDocument` では <xref:System.Text.Json.JsonDocument.RootElement> プロパティが公開されます。

以下のセクションでは、これらのツールを使用して JSON の読み取りと書き込みを行う方法を示します。

## <a name="use-jsondocument-for-access-to-data"></a>JsonDocument を使用してデータにアクセスする

次の例は、<xref:System.Text.Json.JsonDocument> クラスを使用して JSON 文字列内のデータにランダム アクセスする方法を示しています。

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

上記のコードでは次の操作が行われます。

* 分析する JSON が `jsonString` という名前の文字列に含まれていると想定します。
* `Grade` プロパティを持つ `Students` 配列内のオブジェクトの平均グレードを計算します。
* グレードのない学生には既定のグレード 70 を割り当てます。
* 反復するたびに `count` 変数をインクリメントして学生をカウントします。 別の方法として、次の例に示すように <xref:System.Text.Json.JsonElement.GetArrayLength%2A> を呼び出すこともできます。

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

このコードで処理される JSON の例を次に示します。

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a>JsonDocument を使用して JSON を書き込む

次の例では、<xref:System.Text.Json.JsonDocument> から JSON を書き込む方法を示します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

上記のコードでは次の操作が行われます。

* JSON ファイルを読み取り、データを `JsonDocument` に読み込み、書式設定された (整形された) JSON をファイルに書き込みます。
* <xref:System.Text.Json.JsonDocumentOptions> を使用して、入力 JSON 内でコメントは許可されるが無視されることを指定します。
* 完了したら、ライターに対して <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> を呼び出します。 別の方法として、破棄されたときにライターを自動フラッシュすることもできます。

コード例によって処理される JSON 入力の例を次に示します。

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

その結果は、次のような整形された JSON 出力になります。

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a>Utf8JsonWriter を使用する

<xref:System.Text.Json.Utf8JsonWriter> クラスを使用する方法を示す例を次に示します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a>Utf8JsonReader を使用する

<xref:System.Text.Json.Utf8JsonReader> クラスを使用する方法を示す例を次に示します。

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

上記のコードでは、`jsonUtf8` 変数が、UTF-8 としてエンコードされた有効な JSON を含むバイト配列であることを想定しています。

### <a name="filter-data-using-utf8jsonreader"></a>Utf8JsonReader を使用してデータをフィルター処理する

次の例は、ファイルを同期的に読み取り、値を検索する方法を示しています。

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

([この例の非同期バージョン](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs)は利用できます)

上記のコードでは次の操作が行われます。

* JSON にオブジェクトの配列が含まれ、各オブジェクトに文字列型の "name" プロパティが含まれている可能性があると想定します。
* オブジェクトと "University" で終わる "name" プロパティ値をカウントします。
* ファイルが UTF-16 としてエンコードされ、UTF-8 にトランスコードされるものと想定します。 UTF-8 としてエンコードされたファイルは、次のコードを使用して、`ReadOnlySpan<byte>` に直接読み取ることができます。

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  リーダーではテキストが想定されるため、ファイルに UTF-8 バイト オーダー マーク (BOM) が含まれている場合は、バイトを `Utf8JsonReader` に渡す前にそれを削除します。 そうしないと、BOM は無効な JSON と見なされ、リーダーによって例外がスローされます。

上記のコードで読み取ることができる JSON のサンプルを次に示します。 結果として生成される概要メッセージは、"2 out of 4 have names that end with 'University'" です。

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a>Utf8JsonReader を使用してストリームから読み取る

大きなファイル (ギガバイト以上のサイズなど) を読み取る場合、一度にファイル全体をメモリに読み込む必要を回避することができます。 このシナリオでは、<xref:System.IO.FileStream> を使用できます。

`Utf8JsonReader` を使用してストリームから読み取る場合、次の規則が適用されます。

* 部分的な JSON ペイロードが格納されるバッファーは、リーダーが処理を進めることができるように、少なくともその中で最大の JSON トークンと同じ大きさにする必要があります。
* バッファーは、少なくとも JSON 内の空白の最大シーケンスと同じ大きさである必要があります。
* リーダーでは、JSON ペイロード内の次の <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> が完全に読み取られるまで、読み取られたデータが追跡されません。 そのため、バッファー内にバイトが残っている場合は、再びリーダーに渡す必要があります。 <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> を使用して、残っているバイト数を確認できます。

次のコードは、ストリームから読み取る方法を示しています。 この例は、<xref:System.IO.MemoryStream> を示しています。 同様のコードが <xref:System.IO.FileStream> で機能しますが、開始時に UTF-8 BOM が `FileStream` に含まれている場合を除きます。 その場合は、残りのバイトを `Utf8JsonReader` に渡す前に、バッファーからこれらの 3 バイトを取り除く必要があります。 そうしないと、BOM は JSON の有効な部分と見なされないため、リーダーによって例外がスローされます。

このサンプル コードでは、4 KB のバッファーから開始し、サイズが完全な JSON トークンに対応するのに十分な大きさではないことが判明するたびにバッファー サイズを 2 倍にします。これは、リーダーが JSON ペイロードの処理を進めるために必要です。 スニペットに用意されている JSON サンプルでは、非常に小さい初期バッファー サイズ (たとえば、10 バイト) を設定した場合にのみ、バッファー サイズが増加します。 初期バッファー サイズを 10 に設定すると、`Console.WriteLine` ステートメントによって、バッファー サイズの増加の原因と影響が示されます。 4 KB の初期バッファー サイズで、サンプルの JSON 全体が各 `Console.WriteLine` によって表示され、バッファー サイズを増やす必要はありません。

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

前の例では、バッファーを拡大できる最大の大きさを無制限に設定しています。 トークン サイズが大きすぎる場合、コードは <xref:System.OutOfMemoryException> 例外で失敗する可能性があります。 これは、JSON にサイズが約 1 GB 以上のトークンが含まれている場合に発生する可能性があります。1 GB のサイズを 2 倍にすると、サイズが大きすぎて `int32` バッファーに入り切らないためです。

## <a name="additional-resources"></a>その他の技術情報

* [System.Text.Json の概要](system-text-json-overview.md)
* [カスタム コンバーターを記述する方法](system-text-json-converters-how-to.md)
* [Newtonsoft.Json から移行する方法](system-text-json-migrate-from-newtonsoft-how-to.md)
* [System.Text.Json での DateTime と DateTimeOffset のサポート](../datetime/system-text-json-support.md)
* [System.Text.Json API リファレンス](xref:System.Text.Json)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
