---
title: 破壊的変更:Activity.Tags 内のタグの順序が逆になっている
description: Core .NET ライブラリにおける .NET 5.0 の破壊的変更について学習します。Activity.Tags では、追加された順に項目がリストに格納されるようになりました。
ms.date: 11/01/2020
ms.openlocfilehash: 1ff14dc1a4f7a0bf8cf9e79f3750b819f4d4a5ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759444"
---
# <a name="order-of-tags-in-activitytags-is-reversed"></a>Activity.Tags 内のタグの順序が逆になっている

<xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> では、追加された順に項目がリストに格納されるようになりました。つまり、最初に追加された項目がリストの先頭になります。 この変更は、[OpenTelemetry Attributes 仕様](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes)と一致させるために行われました。

## <a name="change-description"></a>変更内容

以前のバージョンの .NET では、<xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> により追加されたのと逆の順序で項目が格納されます。 つまり、最初に追加された項目がリストの末尾になります。 .NET 5.0 以降では、項目の順序は逆になり、最初に追加された項目が常にリストの先頭になります。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

ご使用のアプリが <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> リストの順序に依存していて、.NET 5.0 以降にアップグレードする場合は、コードのこの部分を変更する必要があります。

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Diagnostics.Activity.Tags?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `P:System.Diagnostics.Activity.Tags`

-->
