---
title: 遅延式
description: 'F # のレイジー式を使用して、アプリとライブラリのパフォーマンスを向上させる方法について説明します。'
ms.date: 08/15/2020
ms.openlocfilehash: 0b8496467295ce6793f80c341af88bb1819f4a47
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425504"
---
# <a name="lazy-expressions"></a>遅延式

*レイジー式* は、すぐに評価されるのではなく、結果が必要になったときに評価される式です。 これは、コードのパフォーマンスを向上させるのに役立ちます。

## <a name="syntax"></a>構文

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Remarks

前の構文では、 *expression* は結果が必要な場合にのみ評価されるコードであり、 *identifier* は結果を格納する値です。 値は型であり `Lazy<'T>` 、に使用される実際の型 `'T` は、式の結果から決定されます。

レイジー式を使用すると、式の実行を、結果が必要な状況のみに制限することで、パフォーマンスを向上させることができます。

式を強制的に実行するには、メソッドを呼び出し `Force` ます。 `Force` 実行を1回だけ実行します。 後続のを呼び出すと、 `Force` 同じ結果が返されますが、コードは実行されません。

次のコードは、レイジー式の使用方法との使用方法を示してい `Force` ます。 このコードでは、の型 `result` は `Lazy<int>` で、メソッドはを `Force` 返し `int` ます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

遅延評価は、型ではなく、 `Lazy` シーケンスにも使用されます。 詳細については、「 [シーケンス](sequences.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [LazyExtensions モジュール](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazyextensions.html)
