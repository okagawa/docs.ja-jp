---
title: System.Text.Json で派生クラスのプロパティをシリアル化する方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、ポリモーフィック オブジェクトをシリアル化する方法について説明します。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 4b99a402ea4f4c664d3bfd75627ffaf94948d493
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439791"
---
# <a name="how-to-serialize-properties-of-derived-classes-with-no-locsystemtextjson"></a>System.Text.Json で派生クラスのプロパティをシリアル化する方法

この記事では、`System.Text.Json` 名前空間を使用して派生クラスのプロパティをシリアル化する方法について説明します。

## <a name="serialize-properties-of-derived-classes"></a>派生クラスのプロパティのシリアル化

ポリモーフィック型の階層のシリアル化はサポートされて "_いません_"。 たとえば、プロパティがインターフェイスまたは抽象クラスとして定義されている場合は、ランタイム型に追加のプロパティがある場合でも、インターフェイスまたは抽象クラスに定義されたプロパティのみがシリアル化されます。 この動作の例外については、このセクションで説明します。

たとえば、`WeatherForecast` クラスと派生クラス `WeatherForecastDerived` があるとします。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFDerived":::

また、コンパイル時の `Serialize` メソッドの型引数が `WeatherForecast` であるとします。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeDefault":::

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

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeGetType":::

* オブジェクトを `object` としてシリアル化するように宣言します。

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeObject":::

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

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPrevious":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPreviousAsObject":::

`PreviousForecast` プロパティに `WeatherForecastDerived` のインスタンスが含まれる場合:

* `WeatherForecastWithPrevious` のシリアル化からの JSON 出力には `WindSpeed` が **含まれていません**。
* `WeatherForecastWithPreviousAsObject` のシリアル化からの JSON 出力には `WindSpeed` が **含まれています**。

ルート オブジェクトは派生型である可能性があるものではないため、`WeatherForecastWithPreviousAsObject` をシリアル化するために `Serialize<object>` または `GetType` を呼び出す必要はありません。 次のコード例では `Serialize<object>` または `GetType` は呼び出されません。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeSecondLevel":::

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

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/IForecast.cs":::

`Forecasts` のインスタンスをシリアル化する場合、`Tuesday` は `object` として定義されているので、`Tuesday` にのみ `WindSpeed` プロパティが表示されます。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeInterface":::

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

## <a name="see-also"></a>関連項目

* [System.Text.Json の概要](system-text-json-overview.md)
* [JsonSerializerOptions をインスタンス化する](system-text-json-configure-options.md)
* [大文字と小文字を区別しない一致を有効にする](system-text-json-character-casing.md)
* [プロパティの名前と値をカスタマイズする](system-text-json-customize-properties.md)
* [プロパティを無視する](system-text-json-ignore-properties.md)
* [無効な JSON を許可する](system-text-json-invalid-json.md)
* [オーバーフロー JSON の処理](system-text-json-handle-overflow.md)
* [循環参照の保持](system-text-json-preserve-references.md)
* [変更できない型と非パブリック アクセサー](system-text-json-immutability.md)
* [System.Text.Json API リファレンス](xref:System.Text.Json)
