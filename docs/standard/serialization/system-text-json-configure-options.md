---
title: System.Text.Json で JsonSerializerOptions をインスタンス化する方法
description: 既存のインスタンスをコピーするか Web の既定値を使用して、JsonSerializerOptions インスタンスをインスタンス化する方法について説明します。
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
ms.openlocfilehash: 0febfe15f36856f10699fd327fb17c146277eb9b
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439872"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-no-locsystemtextjson"></a>System.Text.Json で JsonSerializerOptions インスタンスをインスタンス化する方法

この記事では、既存のインスタンスをコピーするか Web の既定値を使用して、<xref:System.Text.Json.JsonSerializerOptions> インスタンスをインスタンス化する方法について説明します。

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

## <a name="see-also"></a>関連項目

* [System.Text.Json の概要](system-text-json-overview.md)
* [大文字と小文字を区別しない一致を有効にする](system-text-json-character-casing.md)
* [プロパティの名前と値をカスタマイズする](system-text-json-customize-properties.md)
* [プロパティを無視する](system-text-json-ignore-properties.md)
* [無効な JSON を許可する](system-text-json-invalid-json.md)
* [オーバーフロー JSON の処理](system-text-json-handle-overflow.md)
* [循環参照の保持](system-text-json-preserve-references.md)
* [変更できない型と非パブリック アクセサー](system-text-json-immutability.md)
* [ポリモーフィックなシリアル化](system-text-json-polymorphism.md)
* [System.Text.Json API リファレンス](xref:System.Text.Json)
