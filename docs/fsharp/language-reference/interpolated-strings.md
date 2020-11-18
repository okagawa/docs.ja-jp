---
title: 挿入文字列
description: '挿入文字列について説明します。これは、F # の式を直接埋め込むことができる特殊な形式の文字列です。'
ms.date: 11/12/2020
ms.openlocfilehash: 8c552b44cea7d6c51ec333b6bdd4d407c6f10da7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829688"
---
# <a name="interpolated-strings"></a>挿入文字列

挿入文字列は、F # の式をその中に埋め込むことができる [文字列](strings.md) です。 これらは、値または式の結果に基づいて文字列の値が変更される可能性があるさまざまなシナリオで役立ちます。

## <a name="syntax"></a>構文

```fsharp
$"string-text {expr}"
$"string-text %format-specifier{expr}"
$"""string-text {"embedded string literal"}"""
```

## <a name="remarks"></a>解説

補間文字列を使用すると、文字列リテラルの内部にコードを "穴" で記述できます。 基本的な例を次に示します。

```fsharp
let name = "Phillip"
let age = 30
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

かっこで囲まれた各ペアの内容は、 `{}` 任意の F # 式にすることができます。

中かっこのペアをエスケープするには `{}` 、次のように2つのペアを記述します。

```fsharp
let str = $"A pair of braces: {{}}"
// "A pair of braces: {}"
```

## <a name="typed-interpolated-strings"></a>型指定された挿入文字列

挿入文字列には、タイプセーフを適用する F # 書式指定子を含めることもできます。

```fsharp
let name = "Phillip"
let age = 30

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

前の例では、コードは、がである必要がある値を誤って渡して `age` `name` います。その逆も同様です。 挿入文字列では書式指定子が使用されるため、これは微妙なランタイムバグではなくコンパイルエラーになります。

[プレーンテキスト形式](plaintext-formatting.md)でカバーされるすべての書式指定子は、挿入文字列内で有効です。

## <a name="verbatim-interpolated-strings"></a>逐語的補間文字列

F # では、文字列リテラルを埋め込むことができるように、三重引用符で逐語的補間文字列をサポートしています。

```fsharp
let age = 30

printfn $"""Name: {"Phillip"}, Age: %d{age}"""
```

## <a name="aligning-expressions-in-interpolated-strings"></a>挿入文字列での式の配置

には、挿入文字列内の式を左揃えまたは右揃えにすることができます。また、スペースの数を指定することもでき `|` ます。 次の補間文字列は、左と右の式をそれぞれ7つのスペースで左右に配置します。

```fsharp
printfn $"""|{"Left",-7}|{"Right",7}|"""
// |Left   |  Right|
```

## <a name="interpolated-strings-and-formattablestring-formatting"></a>挿入文字列と `FormattableString` 書式設定

次の規則に従って書式設定を適用することもでき <xref:System.FormattableString> ます。

```fsharp
let speedOfLight = 299792.458
printfn $"The speed of light is {speedOfLight:N3} km/s."
// "The speed of light is 299,792.458 km/s."
```

また、補間文字列は、型の注釈を使用してとしてチェックされる型にすることもでき <xref:System.FormattableString> ます。

```fsharp
let frmtStr = $"The speed of light is {speedOfLight:N3} km/s." : FormattableString
// Type: FormattableString
// The speed of light is 299,792.458 km/s.
```

型の注釈は、挿入文字列式自体に存在する必要があることに注意してください。 F # は、補間文字列をに暗黙的に変換しません <xref:System.FormattableString> 。

## <a name="see-also"></a>関連項目

* [文字列](strings.md)
