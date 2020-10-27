---
description: C# での void キーワードについて
title: void - C# リファレンス
ms.date: 02/11/2020
f1_keywords:
- void_CSharpKeyword
- void
- (void)
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: fb22fffadeff4db9fcd8e1c8753d44455186aa5a
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471638"
---
# <a name="void-c-reference"></a>void (C# リファレンス)

[メソッド](../../programming-guide/classes-and-structs/methods.md) (または [ローカル関数](../../programming-guide/classes-and-structs/local-functions.md)) が値を返さないことを指定するには、メソッドの戻り値の型として `void` を使用します。

[!code-csharp[void method](snippets/shared/VoidType.cs#VoidExample)]

さらに、不明な型へのポインターを宣言するための参照型として `void` を使用できます。 詳しくは、「[ポインター型](../../programming-guide/unsafe-code-pointers/pointer-types.md)」をご覧ください。

変数の型として `void` を使用することはできません。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- <xref:System.Void?displayProperty=nameWithType>
