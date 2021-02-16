---
title: 基本型
description: 'F # 言語で使用される基本的な基本型について説明します。'
ms.date: 08/15/2020
ms.openlocfilehash: 2bfc9ba9370cb8ba1fcc1d42369c2551cbb57623
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456914"
---
# <a name="basic-types"></a>基本型

このトピックでは、F # 言語で定義されている基本型の一覧を示します。 これらの型は F # で最も基本的なものであり、ほぼすべての F # プログラムの基礎となります。 これらは、.NET プリミティブ型のスーパーセットです。

|Type|.NET の種類|[説明]|例|
|----|---------|-----------|-------|
|`bool`|<xref:System.Boolean>|設定可能な値は `true` および `false` です。|`true`/`false`|
|`byte`|<xref:System.Byte>|0 ~ 255 の値。|`1uy`|
|`sbyte`|<xref:System.SByte>|-128 から127までの値。|`1y`|
|`int16`|<xref:System.Int16>|-32768 から32767までの値。|`1s`|
|`uint16`|<xref:System.UInt16>|0 ~ 65535 の値。|`1us`|
|`int`|<xref:System.Int32>|-2147483648 から2147483647までの値。|`1`|
|`uint`|<xref:System.UInt32>|0 ~ 4294967295 の値。|`1u`|
|`int64`|<xref:System.Int64>|-9223372036854775808 ~ 9223372036854775807 の値。|`1L`|
|`uint64`|<xref:System.UInt64>|0 ~ 18446744073709551615 の値。|`1UL`|
|`nativeint`|<xref:System.IntPtr>|符号付き整数としてのネイティブポインター。|`nativeint 1`|
|`unativeint`|<xref:System.UIntPtr>|符号なし整数としてのネイティブポインター。|`unativeint 1`|
|`decimal`|<xref:System.Decimal>|有効桁数が28以上の浮動小数点データ型。|`1.0`|
|`float`, `double`|<xref:System.Double>|64ビットの浮動小数点型。|`1.0`|
|`float32`, `single`|<xref:System.Single>|32ビットの浮動小数点型。|`1.0f`|
|`char`|<xref:System.Char>|Unicode 文字の値。|`'c'`|
|`string`|<xref:System.String>|Unicode テキスト。|`"str"`|
|`unit`|適用外|実際の値が存在しないことを示します。 型には、示されている仮値が1つだけあり `()` ます。 単位値は、 `()` 値が必要であるものの、実際の値を使用できない、または意味を持つプレースホルダーとしてよく使用されます。|`()`|

> [!NOTE]
> 型を使用して、整数値が64ビット整数型に対して大きすぎる計算を実行でき `bigint` ます。 `bigint` は基本的な型とは見なされません。これは、の省略形です `System.Numerics.BigInteger` 。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
