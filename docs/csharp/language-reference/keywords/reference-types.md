---
description: 参照型 - C# リファレンス
title: 参照型 - C# リファレンス
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: 075ec5ecd8f71f5cb85bab0e2baff56409709191
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899614"
---
# <a name="reference-types-c-reference"></a>参照型 (C# リファレンス)

C# では、参照型と値型という 2 種類の型をサポートしています。 参照型の変数はデータ (オブジェクト) への参照を格納するのに対して、値型の変数はデータを直接格納します。 参照型の場合、2 つの変数が同じオブジェクトを参照できるため、ある変数に対する演算によって、他の変数が参照しているオブジェクトが影響を受ける可能性があります。 値型の場合、各変数が独自のデータ コピーを保持し、ある変数に対する操作が別の変数に影響を与えることはありません (ref および out パラメーター変数の場合を除きます。[in](in-parameter-modifier.md)、[ref](ref.md)、[out](out-parameter-modifier.md) パラメーター修飾子に関するページを参照してください)。

 次のキーワードは、参照型を宣言するときに使用します。

- [class](class.md)

- [interface](interface.md)

- [delegate](../builtin-types/reference-types.md)
- [record](../builtin-types/reference-types.md)

 C# では次の組み込みの参照型も使用できます。

- [dynamic](../builtin-types/reference-types.md)

- [object](../builtin-types/reference-types.md)

- [string](../builtin-types/reference-types.md)

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# のキーワード](index.md)
- [ポインター型](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [値型](../builtin-types/value-types.md)
