---
title: System.Text.Json で文字エンコードをカスタマイズする方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、文字エンコードをカスタマイズする方法について説明します。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: f6a50a3ca2a5e871294cf7c056cbf197a61cd668
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439807"
---
# <a name="how-to-customize-character-encoding-with-no-locsystemtextjson"></a>System.Text.Json で文字エンコードをカスタマイズする方法

既定では、シリアライザーでは ASCII 以外のすべての文字がエスケープされます。 つまり、`\uxxxx` に置き換えられます。`xxxx` は文字の Unicode コードです。 たとえば、次の JSON の `Summary` プロパティがキリル文字の `жарко` に設定されている場合、`WeatherForecast` オブジェクトは次の例に示すようにシリアル化されます。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

## <a name="serialize-language-character-sets"></a>言語文字セットのシリアル化

1 つ以上の言語の文字セットをエスケープせずにシリアル化するには、次の例に示すように、<xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> のインスタンスを作成するときに [Unicode 範囲](xref:System.Text.Unicode.UnicodeRanges)を指定します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="LanguageSets":::

このコードでは、キリル文字やギリシャ文字はエスケープされません。 `Summary` プロパティがキリル文字の `жарко` に設定されている場合、`WeatherForecast` オブジェクトは次の例に示すようにシリアル化されます。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

すべての言語セットをエスケープせずにシリアル化するには、<xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> を使用します。

## <a name="serialize-specific-characters"></a>特定の文字のシリアル化

別の方法として、エスケープせずに許可する個々の文字を指定することもできます。 次の例では、`жарко` の最初の 2 文字のみをシリアル化します。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="SelectedCharacters":::

上記のコードによって生成される JSON の例を次に示します。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

## <a name="serialize-all-characters"></a>すべての文字のシリアル化

エスケープを最小化するには、次の例に示すように、<xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> を使用できます。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="UnsafeRelaxed":::

> [!CAUTION]
> 既定のエンコーダーと比較して、`UnsafeRelaxedJsonEscaping` エンコーダーは、文字をエスケープせずにそのまま渡すことについて、より寛容です。
>
> * `<`、`>`、`&`、`'` など、HTML に影響する文字はエスケープされません。
> * クライアントとサーバーが "*文字セット*" について合意していない場合の結果など、XSS または情報漏えい攻撃に対する追加の多層防御は提供されません。
>
> 安全でないエンコーダーは、クライアントによって結果のペイロードが UTF-8 でエンコードされた JSON として解釈されることがわかっている場合にのみ使用してください。 たとえば、サーバーが応答ヘッダー `Content-Type: application/json; charset=utf-8` を送信している場合は使用できます。 未加工の `UnsafeRelaxedJsonEscaping` 出力が HTML ページまたは `<script>` 要素に決して出力されないようにしてください。

## <a name="see-also"></a>関連項目

* [System.Text.Json の概要](system-text-json-overview.md)
* [カスタム シリアライザーと逆シリアライザーを作成する方法](write-custom-serializer-deserializer.md)
* [JSON シリアル化のためのカスタム コンバーターを作成する方法](system-text-json-converters-how-to.md)
* [System.Text.Json API リファレンス](xref:System.Text.Json)
