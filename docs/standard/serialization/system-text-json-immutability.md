---
title: System.Text.Json で変更できない型と非パブリック アクセサーを使用する方法
description: .NET で JSON との間のシリアル化および逆シリアル化を行うときに、変更できない型と非パブリック アクセサーを使用する方法について説明します。
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
ms.openlocfilehash: d3e61d44ce22b7f50838b6d3ba9cf64004bd3725
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439786"
---
# <a name="how-to-use-immutable-types-and-non-public-accessors-with-no-locsystemtextjson"></a>System.Text.Json で変更できない型と非パブリック アクセサーを使用する方法

この記事では、`System.Text.Json` 名前空間を使用して、レコードなどの変更できない型を使用する方法について説明します。

## <a name="immutable-types-and-records"></a>不変の型とレコード

::: zone pivot="dotnet-5-0"
`System.Text.Json` ではパラメーター化されたコンストラクターを使用できるので、不変のクラスまたは構造体を逆シリアル化できます。 クラスの場合、パラメーター化されたコンストラクターしかない場合は、そのコンストラクターが使用されます。 構造体または複数のコンストラクターを持つクラスの場合は、[[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) 属性を適用することにより、使用するコンストラクターを指定します。 その属性を使用しないと、パラメーターなしのパブリック コンストラクターが存在する場合は常にそれが使用されます。 その属性は、パブリック コンストラクターでのみ使用できます。 次の例では、`[JsonConstructor]` 属性が使用されています。

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

## <a name="see-also"></a>関連項目

* [System.Text.Json の概要](system-text-json-overview.md)
* [JsonSerializerOptions をインスタンス化する](system-text-json-configure-options.md)
* [大文字と小文字を区別しない一致を有効にする](system-text-json-character-casing.md)
* [プロパティの名前と値をカスタマイズする](system-text-json-customize-properties.md)
* [プロパティを無視する](system-text-json-ignore-properties.md)
* [無効な JSON を許可する](system-text-json-invalid-json.md)
* [オーバーフロー JSON の処理](system-text-json-handle-overflow.md)
* [循環参照の保持](system-text-json-preserve-references.md)
* [ポリモーフィックなシリアル化](system-text-json-polymorphism.md)
* [System.Text.Json API リファレンス](xref:System.Text.Json)
