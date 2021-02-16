---
description: "詳細情報: BC36532:入れ子になった関数に、デリゲート '<delegatename>' と互換性のあるシグネチャがありません。"
title: 入れ子になった関数に、デリゲート '<delegatename>' と互換性のあるシグネチャがありません。
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: ff6abda015187d0d7d0690f2f1fd00772e63c61b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483548"
---
# <a name="bc36532-nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a>BC36532:入れ子になった関数に、デリゲート '\<delegatename>' と互換性のあるシグネチャがありません。

ラムダ式が、互換性のないシグネチャを含むデリゲートに割り当てられています。 たとえば、次のコードでは、デリゲート `Del` に 2 つの整数パラメーターがあります。

```vb
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer
```

このエラーは、1 つの引数を含むラムダ式が `Del` 型として宣言されている場合に発生します。

```vb
' Neither of these is valid.
' Dim lambda1 As Del = Function(n As Integer) n + 1
' Dim lambda2 As Del = Function(n) n + 1
```

**エラー ID:** BC36532

## <a name="to-correct-this-error"></a>このエラーを解決するには

デリゲート定義または割り当てられているラムダ式を調整して、シグネチャに互換性を持たせるようにします。

## <a name="see-also"></a>関連項目

- [厳密でないデリゲート変換](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [ラムダ式](../../programming-guide/language-features/procedures/lambda-expressions.md)
