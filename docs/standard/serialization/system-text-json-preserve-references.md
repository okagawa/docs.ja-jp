---
title: System.Text.Json で参照を保持する方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、参照を保持し、循環参照を処理する方法について説明します。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 9254ca261c7d748c04c311fa56359014f752ff31
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439788"
---
# <a name="how-to-handle-circular-references-with-no-locsystemtextjson"></a>System.Text.Json で循環参照を処理する方法

この記事では、`System.Text.Json` 名前空間を使用して循環参照を処理する方法について説明します。

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

## <a name="see-also"></a>関連項目

* [System.Text.Json の概要](system-text-json-overview.md)
* [JsonSerializerOptions をインスタンス化する](system-text-json-configure-options.md)
* [大文字と小文字を区別しない一致を有効にする](system-text-json-character-casing.md)
* [プロパティの名前と値をカスタマイズする](system-text-json-customize-properties.md)
* [プロパティを無視する](system-text-json-ignore-properties.md)
* [無効な JSON を許可する](system-text-json-invalid-json.md)
* [オーバーフロー JSON の処理](system-text-json-handle-overflow.md)
* [変更できない型と非パブリック アクセサー](system-text-json-immutability.md)
* [ポリモーフィックなシリアル化](system-text-json-polymorphism.md)
* [System.Text.Json API リファレンス](xref:System.Text.Json)
