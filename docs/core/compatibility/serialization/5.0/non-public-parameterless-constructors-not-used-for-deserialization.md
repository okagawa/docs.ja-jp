---
title: 破壊的変更:非パブリック、パラメーターなしのコンストラクターが逆シリアル化に使用されない
description: .NET 5.0 での破壊的変更について学習します。JsonSerializer で非パブリック、パラメーターなしのコンストラクターが逆シリアル化に使用されなくなりました。
ms.date: 10/18/2020
ms.openlocfilehash: a2ea54b6a76692dae7d6e01b06b11218d66b1cd7
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794702"
---
# <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a>非パブリック、パラメーターなしのコンストラクターが逆シリアル化に使用されない

サポートされているすべてのターゲット フレームワーク モニカー (TFM) との間で一貫性を維持するために、既定では、非パブリックのパラメーターなしのコンストラクターは <xref:System.Text.Json.JsonSerializer> での逆シリアル化に使用されなくなりました。

## <a name="change-description"></a>変更内容

.NET Standard 2.0 以降をサポートするスタンドアロン [System.Text.Json NuGet パッケージ](https://www.nuget.org/packages/System.Text.Json/) (つまり、バージョン 4.6.0-4.7.2) の動作は、.NET Core 3.0 および 3.1 の組み込みの動作と一致しません。 .NET Core 3.x では、internal と private コンストラクターを逆シリアル化に使用できます。 スタンドアロン パッケージで、非パブリック コンストラクターは使用できません。また、非パブリックのパラメーターなしのコンストラクターが定義されていない場合は、<xref:System.MissingMethodException> がスローされます。

.NET 5.0 以降および System.Text.Json NuGet パッケージ 5.0.0 では、NuGet パッケージと組み込み API 間で動作に一貫性があります。 非パブリック コンストラクター (パラメーターなしのコンストラクターを含む) は、既定ではシリアライザーによって無視されます。 逆シリアル化のために、次のいずれかのコンストラクターがシリアライザーによって使用されます。

- <xref:System.Text.Json.Serialization.JsonConstructorAttribute> の注釈が付けられたパブリック コンストラクター。
- パブリックのパラメーターなしのコンストラクター。
- パブリックのパラメーター化されたコンストラクター (唯一のパブリック コンストラクターが存在する場合)。

これらのコンストラクターをいずれも使用できない場合は、型を逆シリアル化しようとすると <xref:System.NotSupportedException> がスローされます。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="reason-for-change"></a>変更理由

- <xref:System.Text.Json?displayProperty=fullName> のビルド対象のすべてのターゲット フレームワーク モニカー (TFM) の間で一貫した動作を適用するため (.NET Core 3.0 以降のバージョンと .NET Standard 2.0)
- コンストラクター、プロパティ、またはフィールドのいずれであるかにかかわらず、<xref:System.Text.Json.JsonSerializer> から型の非パブリック アクセス領域を呼び出すことができないため。

## <a name="recommended-action"></a>推奨される操作

- 型を所有していて、それが実行可能な場合は、パラメーターなしのコンストラクターをパブリックにします。
- それ以外の場合は、型に対して <xref:System.Text.Json.Serialization.JsonConverter%601> を実装し、逆シリアル化動作を制御します。 そのシナリオの C# アクセシビリティ規則で許可されている場合は、<xref:System.Text.Json.Serialization.JsonConverter%601> の実装から非パブリック コンストラクターを呼び出すことができます。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

Serialization

-->
