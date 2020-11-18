---
title: TimeOffset support in での DateTime と DateTimeOffset のサポート
description: System.Text.Jsのライブラリでの DateTime 型と DateTimeOffset 型のサポートの概要について説明します。
author: layomia
ms.author: laakinri
ms.date: 07/22/2019
helpviewer_keywords:
- JSON, Serializer, Utf8
- JSON DateTime, JSON DateTimeOffset
- DateTime, DateTimeOffset
- JsonSerializer, Utf8JsonReader, Utf8JsonWriter, JsonElement, JsonDocument
- JSON Serializer, JSON Reader, JSON Writer
- Converter, JSON Converter, DateTime Converter
- ISO, ISO 8601, ISO 8601-1:2019
ms.openlocfilehash: 3f8161c40f21428a4a22bef09582754069f3a2b6
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817537"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>TimeOffset support in での DateTime と DateTimeOffset のサポート

ライブラリの System.Text.Jsは、 <xref:System.DateTime> <xref:System.DateTimeOffset> ISO 8601:-2019 拡張プロファイルに従って、との値を解析して書き込みます。
[コンバーター](xref:System.Text.Json.Serialization.JsonConverter%601) は、を使用したシリアル化と逆シリアル化のためのカスタムサポートを提供 <xref:System.Text.Json.JsonSerializer> します。
およびを使用する場合は、カスタムサポートを実装することもでき <xref:System.Text.Json.Utf8JsonReader> <xref:System.Text.Json.Utf8JsonWriter> ます。

## <a name="support-for-the-iso-8601-12019-format"></a>ISO 8601-1:2019 形式のサポート

、、、およびの各型は、 <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.Utf8JsonReader> <xref:System.Text.Json.Utf8JsonWriter> <xref:System.Text.Json.JsonElement> <xref:System.DateTime> <xref:System.DateTimeOffset> ISO 8601-1:2019 形式の拡張プロファイルに従って、解析および書き込みとテキスト表現を行います。たとえば、2019-07-26t16:59:57-05:00 のようになります。

<xref:System.DateTime> および <xref:System.DateTimeOffset> データは、次の方法でシリアル化でき <xref:System.Text.Json.JsonSerializer> ます。

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

また、次のようにして逆シリアル化することもでき <xref:System.Text.Json.JsonSerializer> ます。

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

既定のオプションでは、入力 <xref:System.DateTime> および <xref:System.DateTimeOffset> テキスト表現は拡張 ISO 8601-1:2019 プロファイルに準拠している必要があります。
プロファイルに準拠していない表現を逆シリアル化しようとすると、がスローされ <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonException> ます。

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

は、 <xref:System.Text.Json.JsonDocument> JSON ペイロードの内容 (や表現を含む) への構造化されたアクセスを提供し <xref:System.DateTime> <xref:System.DateTimeOffset> ます。 次の例では、温度のコレクションを指定した場合に、月曜日の平均温度を計算できる方法を示しています。

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

準拠していない形式のペイロードで平均温度を計算しようとすると、がを <xref:System.DateTime> <xref:System.Text.Json.JsonDocument> スローし <xref:System.FormatException> ます。

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

下位レベルの <xref:System.Text.Json.Utf8JsonWriter> 書き込み <xref:System.DateTime> と <xref:System.DateTimeOffset> データ:

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<xref:System.Text.Json.Utf8JsonReader><xref:System.DateTime>とデータを解析し <xref:System.DateTimeOffset> ます。

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

に準拠していない形式を読み取ろうとすると <xref:System.Text.Json.Utf8JsonReader> 、がスローされ <xref:System.FormatException> ます。

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a>およびのカスタムサポート <xref:System.DateTime><xref:System.DateTimeOffset>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a>使用する場合 <xref:System.Text.Json.JsonSerializer>

シリアライザーでカスタムの解析または書式設定を実行する場合は、 [カスタムコンバーター](xref:System.Text.Json.Serialization.JsonConverter%601)を実装できます。
次に例をいくつか示します。

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>およびを使用する `DateTime(Offset).Parse``DateTime(Offset).ToString`

入力またはテキスト表現の形式を特定できない場合は <xref:System.DateTime> <xref:System.DateTimeOffset> 、 `DateTime(Offset).Parse` コンバーターの読み取りロジックでメソッドを使用できます。 これにより、を使用できるようになります。さまざまな <xref:System.DateTime> 形式とテキスト形式のサポート <xref:System.DateTimeOffset> (iso 8601 以外の文字列や iso 8601 形式の拡張 iso 8601-1:2019 プロファイルに準拠していないなど) のサポート。 この方法では、シリアライザーのネイティブ実装よりもパフォーマンスが大幅に低下します。

シリアル化の場合は、 `DateTime(Offset).ToString` コンバーターの書き込みロジックでメソッドを使用できます。 これにより、 <xref:System.DateTime> 標準の <xref:System.DateTimeOffset> [日付と時刻の形式](../base-types/standard-date-and-time-format-strings.md)、および [カスタムの日付と時刻](../base-types/custom-date-and-time-format-strings.md)の書式を使用して、との値を書き込むことができます。
これは、シリアライザーのネイティブ実装を使用する場合よりも、パフォーマンスが大幅に低下します。

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> を実装するとき、およびがの場合、 <xref:System.Text.Json.Serialization.JsonConverter%601> `T` パラメーターは <xref:System.DateTime> `typeToConvert` 常にになり `typeof(DateTime)` ます。
パラメーターは、ポリモーフィックなケースを処理する場合や、ジェネリックを使用してパフォーマンスの高い方法を実現する場合に便利です `typeof(T)` 。

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a>およびを使用する <xref:System.Buffers.Text.Utf8Parser><xref:System.Buffers.Text.Utf8Formatter>

入力 <xref:System.DateTime> または <xref:System.DateTimeOffset> テキスト表現が "R"、"l"、"O"、"G" のいずれかの [日付/時刻書式指定文字列](../base-types/standard-date-and-time-format-strings.md)に準拠している場合、またはこれらの形式のいずれかに従って記述する場合は、コンバーターロジックで utf-8 ベースの高速な解析および書式指定メソッドを使用できます。 これは、およびを使用するよりもはるかに高速です `DateTime(Offset).Parse` `DateTime(Offset).ToString` 。

次の例は、 <xref:System.DateTime> ["R" 標準形式](../base-types/standard-date-and-time-format-strings.md#the-rfc1123-r-r-format-specifier)に従って値をシリアル化および逆シリアル化するカスタムコンバーターを示しています。

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> "R" 標準形式の長さは常に29文字です。
>
> "L" (小文字の "L") 形式は、および型でのみサポートされているため、他の [標準の日時書式指定文字列](../base-types/standard-date-and-time-format-strings.md) には記載されていません `Utf8Parser` `Utf8Formatter` 。 形式は、小文字の RFC 1123 ("R" 形式の小文字バージョン) です。たとえば、"thu, 25 月 2019 06:36:07 gmt" のようになります。

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>`DateTime(Offset).Parse`シリアライザーのネイティブ解析へのフォールバックとしての使用

通常、入力 <xref:System.DateTime> またはデータが <xref:System.DateTimeOffset> 拡張 ISO 8601-1:2019 プロファイルに準拠していることが予想される場合は、シリアライザーのネイティブ解析ロジックを使用できます。 また、場合によっては、フォールバックメカニズムを実装することもできます。
この例では、を使用してテキスト表現の解析に失敗した後に、 <xref:System.DateTime> <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)> コンバーターがを使用してデータを正常に解析することを示して <xref:System.DateTime.Parse(System.String)> います。

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a>書き込み時に <xref:System.Text.Json.Utf8JsonWriter>

でカスタムまたはテキスト表現を記述する場合は、 <xref:System.DateTime> <xref:System.DateTimeOffset> <xref:System.Text.Json.Utf8JsonWriter> カスタム表現を <xref:System.String> 、、 `ReadOnlySpan<Byte>` 、またはに書式設定 `ReadOnlySpan<Char>` <xref:System.Text.Json.JsonEncodedText> し、それを対応するメソッドまたはメソッドに渡すことができ <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A?displayProperty=nameWithType> <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A?displayProperty=nameWithType> ます。

次の例では、を使用してカスタム <xref:System.DateTime> 書式を作成 <xref:System.DateTime.ToString(System.String,System.IFormatProvider)> し、メソッドを使用して記述する方法を示し <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> ます。

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a>読み取り時の <xref:System.Text.Json.Utf8JsonReader>

を使用してカスタムまたはテキスト表現を読み取る場合は、 <xref:System.DateTime> <xref:System.DateTimeOffset> 現在の <xref:System.Text.Json.Utf8JsonReader> JSON トークンの値をを使用して取得し <xref:System.String> 、その値を <xref:System.Text.Json.Utf8JsonReader.GetString> カスタムロジックを使用して解析することができます。

次の例は、を使用してカスタム <xref:System.DateTimeOffset> テキスト表現を取得し <xref:System.Text.Json.Utf8JsonReader.GetString> 、を使用して解析する方法を示してい <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)> ます。

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>System.Text.Jsの拡張 ISO 8601-1:2019 プロファイル

### <a name="date-and-time-components"></a>日付と時刻のコンポーネント

で実装されている拡張 ISO 8601-1:2019 プロファイルは、 <xref:System.Text.Json> 日付と時刻の表現に関して次のコンポーネントを定義します。 これらのコンポーネントは、解析と書式設定および表現の際にサポートされるさまざまな粒度レベルを定義するために使用され <xref:System.DateTime> <xref:System.DateTimeOffset> ます。

| コンポーネント       | Format                      | 説明                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| 年            | "yyyy"                      | 0001-9999                                                                       |
| Month           | "MM"                        | 01-12                                                                           |
| 日             | "dd"                        | 01-28、01-29、01-30、01-31 (月/年)                                  |
| 時間            | "HH"                        | 00-23                                                                           |
| 分          | "mm"                        | 00-59                                                                           |
| Second          | "ss"                        | 00-59                                                                           |
| 2番目の分数 | "FFFFFFF"                   | 最低1桁、最大16桁                                      |
| 時間のオフセット     | "K"                         | "Z" または "(' + '/'-') HH ': ' mm '                                                |
| 部分的な時間    | "HH ': ' mm ': ' ss [FFFFFFF]"     | UTC オフセット情報なしの時間                                             |
| 完全な日付       | "yyyy'-'mm'-'dd't'hh-' MM'-' dd"            | カレンダーの日付                                                                   |
| フルタイム       | "Partial time'K"           | 現地時刻と UTC の時差を使用した日の UTC または現地時刻 |
| 日時       | "' 完全な日付 ' ' ' ' ' ' ' は完全な時刻 '" になります。 | カレンダーの日付と時刻。例: 2019-07-26T16:59:57-05:00                   |

### <a name="support-for-parsing"></a>解析のサポート

解析のために次の粒度のレベルが定義されています。

1. ' 完全な日付 '
    1. "yyyy'-'mm'-'dd't'hh-' MM'-' dd"

2. "' Full date ' ' ' Hour ' ': ' ' Minute '"
    1. "yyyy'-'mm'-'dd't'hh-' MM'-' + ': ' MM '

3. "' 完全な日付 ' t ' ' Partial time '"
    1. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss ' ([並べ替え可能な (" s ") 書式指定子](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))
    2. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFF

4. "' Full date ' ' ' Time Time ' ': ' ' Minute ' ' Time offset '"
    1. "yyyy'-'mm'-'dd't'hh-" MM'-' Dd' T' HH ': ' mmZ "
    2. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' Hh ': ' mm (' + '/'-') HH ': ' mm '

5. ' 日時 '
    1. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ssZ '
    2. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFFZ "
    3. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' mm ': ' ss (' + '/'-') HH ': ' mm '
    4. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFF (' + '/'-') HH ': ' mm "

    このレベルの粒度は、 [RFC 3339](https://tools.ietf.org/html/rfc3339#section-5.6)に準拠しています。これは、日付と時刻の情報を交換するために使用される ISO 8601 の広く採用されたプロファイルです。 ただし、実装の System.Text.Jsにはいくつかの制限があります。

    - RFC 3339 では、秒の小数部の最大桁数が指定されていませんが、秒の小数部が存在する場合は、少なくとも1つの数字がピリオドの後に続く必要があることを指定します。 System.Text.Jsでのの実装では、(他のプログラミング言語やフレームワークとの相互運用をサポートするために) 最大16桁まで使用できますが、最初の7つだけを解析します。 <xref:System.Text.Json.JsonException>とのインスタンスを読み取るときに、秒の小数点以下桁数が16を超えると、がスローされ `DateTime` `DateTimeOffset` ます。
    - RFC 3339 では、"T" と "Z" の文字をそれぞれ "t" または "z" にすることができますが、アプリケーションでサポートを大文字のバリアントのみに制限することができます。 System.Text.Jsでの実装では、"T" および "Z" である必要があります。 <xref:System.Text.Json.JsonException>とのインスタンスを読み取るときに、入力ペイロードに "t" または "z" が含まれている場合は、がスローされ `DateTime` `DateTimeOffset` ます。
    - RFC 3339 では、日付と時刻のセクションを "T" で区切って指定しますが、アプリケーションでは、代わりにスペース ("") で区切ることができます。 の System.Text.Jsでは、日付と時刻のセクションを "T" で区切る必要があります。 <xref:System.Text.Json.JsonException>とのインスタンスを読み取るときに、入力ペイロードにスペース ("") が含まれていると、がスローされ `DateTime` `DateTimeOffset` ます。

秒の小数部がある場合は、少なくとも1つの数字が必要です。 `2019-07-26T00:00:00.` は使用できません。
最大16桁の小数部を使用できますが、最初の7だけが解析されます。 それを超えるものはゼロと見なされます。
たとえば、はの `2019-07-26T00:00:00.1234567890` ように解析され `2019-07-26T00:00:00.1234567` ます。
これは、 <xref:System.DateTime> この解決に限定された実装との互換性を維持するためのものです。

うるう秒はサポートされていません。

### <a name="support-for-formatting"></a>書式設定のサポート

次の粒度レベルは、書式設定のために定義されています。

1. "' 完全な日付 ' t ' ' Partial time '"
    1. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss ' ([並べ替え可能な (" s ") 書式指定子](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))

        <xref:System.DateTime>秒の小数部を含まない、オフセット情報を使用せずに、を書式設定するために使用します。

    2. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFF

        <xref:System.DateTime>秒の小数部のオフセット情報を使用せずに、を書式設定するために使用します。

2. ' 日時 '
    1. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ssZ '

        秒単位ではなく、UTC オフセットを使用して、を書式設定するために使用 <xref:System.DateTime> します。

    2. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFFZ "

        秒の小数部を UTC オフセットで書式設定するために使用し <xref:System.DateTime> ます。

    3. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' mm ': ' ss (' + '/'-') HH ': ' mm '

        <xref:System.DateTime>秒の小数部を含まない、またはローカルオフセットを使用して、またはの書式を設定するために使用 <xref:System.DateTimeOffset> します。

    4. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFF (' + '/'-') HH ': ' mm "

        <xref:System.DateTime>秒の小数部とローカルオフセットを使用して、またはの書式を設定するために使用し <xref:System.DateTimeOffset> ます。

    このレベルの粒度は、 [RFC 3339](https://tools.ietf.org/html/rfc3339#section-5.6)に準拠しています。

またはインスタンスの [ラウンドトリップ形式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) 表現の <xref:System.DateTime> <xref:System.DateTimeOffset> 秒の小数部に後続のゼロがある場合、 <xref:System.Text.Json.JsonSerializer> とは、末尾に0を <xref:System.Text.Json.Utf8JsonWriter> 付けずにインスタンスの表現を書式設定します。
たとえば、 <xref:System.DateTime> [ラウンドトリップ形式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) 表現がであるインスタンスは、 `2019-04-24T14:50:17.1010000Z` とによって書式設定され `2019-04-24T14:50:17.101Z` <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.Utf8JsonWriter> ます。

またはインスタンスの [ラウンドトリップ形式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) 表現で <xref:System.DateTime> 、 <xref:System.DateTimeOffset> 秒の小数部にゼロがすべて含まれている場合、 <xref:System.Text.Json.JsonSerializer> と <xref:System.Text.Json.Utf8JsonWriter> は秒の小数部なしでインスタンスの表現を書式設定します。
たとえば、 <xref:System.DateTime> [ラウンドトリップ形式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) 表現がであるインスタンスは、 `2019-04-24T14:50:17.0000000+02:00` とによって書式設定され `2019-04-24T14:50:17+02:00` <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.Utf8JsonWriter> ます。

秒の小数点以下桁数で0を切り捨てた場合、書き込まれるラウンドトリップに関する情報を保持するために必要な最小の出力が可能になります。

最大7桁の小数点以下桁数が書き込まれます。 これ <xref:System.DateTime> は、この解決に限定される実装に合わせて配置されます。
