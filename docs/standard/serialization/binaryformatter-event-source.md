---
title: BinaryFormatter イベント ソース
description: シリアル化または逆シリアル化が発生したときに、BinaryFormatter イベント ソースを使用してログを記録する方法について説明します。
ms.date: 12/03/2020
ms.author: levib
author: GrabYourPitchforks
ms.openlocfilehash: 9ae2af77b6cfc270207fb0f2969ada8c2eca1153
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740390"
---
# <a name="binaryformatter-event-source"></a>BinaryFormatter イベント ソース

.NET 5.0 以降、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> には、オブジェクトのシリアル化または逆シリアル化が発生したタイミングを可視化できる、組み込みの <xref:System.Diagnostics.Tracing.EventSource> が含まれています。 アプリでは、<xref:System.Diagnostics.Tracing.EventListener> から派生した型を使用してこれらの通知をリッスンし、ログに記録できます。

この機能は <xref:System.Runtime.Serialization.SerializationBinder> または <xref:System.Runtime.Serialization.ISerializationSurrogate> に代わるものではなく、シリアル化または逆シリアル化されるデータを変更するために使用することはできません。 むしろ、このイベント システムは、シリアル化または逆シリアル化される型についての分析情報を提供することを目的としています。 また、`BinaryFormatter` インフラストラクチャへの意図しない呼び出し (サード パーティ製のライブラリ コードからの呼び出しなど) を検出するために使用することもできます。

## <a name="description-of-events"></a>イベントの説明

`BinaryFormatter` イベント ソースには、`System.Runtime.Serialization.Formatters.Binary.BinaryFormatterEventSource` という既知の名前があります。 リスナーは 6 つのイベントをサブスクライブできます。

### <a name="serializationstart-event-id--10"></a>SerializationStart イベント (id = `10`)

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> が呼び出され、シリアル化プロセスが開始されたときに発生します。 このイベントは、`SerializationEnd` イベントとペアになります。 `SerializationStart` イベントは、オブジェクトがそれ自体のシリアル化ルーチン内で `BinaryFormatter.Serialize` を呼び出す場合、再帰的に呼び出される可能性があります。

このイベントにはペイロードが含まれていません。

### <a name="serializationend-event-id--11"></a>SerializationEnd イベント (id = `11`)

`BinaryFormatter.Serialize` の処理が完了したときに発生します。 `SerializationEnd` が発生するたびに、最後のペアになっていない `SerializationStart` イベントが完了したことがわかります。

このイベントにはペイロードが含まれていません。

### <a name="serializingobject-event-id--12"></a>SerializingObject イベント (id = `12`)

`BinaryFormatter.Serialize` によって非プリミティブ型をシリアル化する処理が行われているときに発生します。 `BinaryFormatter` インフラストラクチャでは特定の型 (`string` や `int` など) が特別なケースとして処理され、これらの型が検出されてもこのイベントは発生しません。 このイベントは、ユーザー定義型、および `BinaryFormatter` によってネイティブに認識されないその他の型に対して発生します。

このイベントは、`SerializationStart` イベントと `SerializationEnd` イベントの間で 0 回以上発生する可能性があります。

このイベントには、1 つの引数を持つペイロードが含まれます。

* `typeName` (`string`):シリアル化される型のアセンブリ修飾名 (<xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> を参照)。

### <a name="deserializationstart-event-id--20"></a>DeserializationStart イベント (id = `20`)

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> が呼び出され、逆シリアル化プロセスが開始されたときに発生します。 このイベントは、`DeserializationEnd` イベントとペアになります。 `DeserializationStart` イベントは、オブジェクトがそれ自体の逆シリアル化ルーチン内で `BinaryFormatter.Deserialize` を呼び出す場合、再帰的に呼び出される可能性があります。

このイベントにはペイロードが含まれていません。

### <a name="deserializationend-event-id--21"></a>DeserializationEnd イベント (id = `21`)

`BinaryFormatter.Deserialize` の処理が完了したときに発生します。 `DeserializationEnd` が発生するたびに、最後のペアになっていない `DeserializationStart` イベントが完了したことがわかります。

このイベントにはペイロードが含まれていません。

### <a name="deserializingobject-event-id--22"></a>DeserializingObject イベント (id = `22`)

`BinaryFormatter.Deserialize` によって非プリミティブ型を逆シリアル化する処理が行われているときに発生します。 `BinaryFormatter` インフラストラクチャでは特定の型 (`string` や `int` など) が特別なケースとして処理され、これらの型が検出されてもこのイベントは発生しません。 このイベントは、ユーザー定義型、および `BinaryFormatter` によってネイティブに認識されないその他の型に対して発生します。

このイベントは、`DeserializationStart` イベントと `DeserializationEnd` イベントの間で 0 回以上発生する可能性があります。

このイベントには、1 つの引数を持つペイロードが含まれます。

* `typeName` (`string`):逆シリアル化される型のアセンブリ修飾名 (<xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> を参照)。

### <a name="advanced-subscribing-to-a-subset-of-notifications"></a>\[高度な設定\] 通知のサブセットをサブスクライブする

通知のサブセットのみをサブスクライブする必要があるリスナーでは、有効にするキーワードを選択できます。

* `Serialization` = `(EventKeywords)1`:`SerializationStart`、`SerializationEnd`、および `SerializingObject` イベントが発生します。
* `Deserialization` = `(EventKeywords)2`:`DeserializationStart`、`DeserializationEnd`、および `DeserializingObject` イベントが発生します。

`EventListener` の登録時にキーワード フィルターが指定されていない場合は、すべてのイベントが発生します。

詳細については、「<xref:System.Diagnostics.Tracing.EventKeywords?displayProperty=nameWithType>」を参照してください。

## <a name="sample-code"></a>サンプル コード

コード例を次に示します。

- `System.Console` に書き込む `EventListener` から派生した型を作成します。
- そのリスナーを `BinaryFormatter` によって生成された通知にサブスクライブします。
- `BinaryFormatter` を使用してシンプルなオブジェクト グラフをシリアル化および逆シリアル化します。
- 発生したイベントを分析します。

:::code language="csharp" source="snippets/binaryformatter-event-source/csharp/Program.cs":::

上記のコードにより、次の例のような出力が生成されます。

```output
Event SerializationStart (id=10) received.
Event SerializingObject (id=12) received.
typeName = BinaryFormatterEventSample.Person, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event SerializingObject (id=12) received.
typeName = BinaryFormatterEventSample.Book, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event SerializationStop (id=11) received.
Event DeserializationStart (id=20) received.
Event DeserializingObject (id=22) received.
typeName = BinaryFormatterEventSample.Person, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event DeserializingObject (id=22) received.
typeName = BinaryFormatterEventSample.Book, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event DeserializationStop (id=21) received.
Rehydrated person Logan Edwards
Favorite book: A Tale of Two Cities by Charles Dickens, list price 10.25
```

このサンプルでは、コンソール ベースの `EventListener` によって、シリアル化が開始され、`Person` と `Book` のインスタンスがシリアル化された後、シリアル化が完了することがログに記録されます。 同様に、逆シリアル化が開始されると、`Person` と `Book` のインスタンスが逆シリアル化された後、逆シリアル化が完了します。

アプリでは次に、逆シリアル化された `Person` に含まれている値が出力され、オブジェクトが実際にシリアル化および逆シリアル化されたことが示されます。

## <a name="see-also"></a>関連項目

`EventListener` を使用して `EventSource` ベースの通知を受信する方法の詳細については、[`EventListener` クラス](xref:System.Diagnostics.Tracing.EventListener)に関する記事を参照してください。
