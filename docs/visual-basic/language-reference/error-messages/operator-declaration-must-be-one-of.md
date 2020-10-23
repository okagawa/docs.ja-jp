---
title: '演算子宣言は次のいずれかでなければなりません: +、-、*、\、/、^、&amp;、Like、Mod、And、Or、Xor、Not、<<、>>、=、<>、<、<=、>、>=、CType、IsTrue、または IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: a94e62e33427987a302a6244b2b8ce8d295e4f11
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159899"
---
# <a name="bc33000-operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a>BC33000:演算子宣言は次のいずれかでなければなりません: +、-、*、\,/、^、&amp;、Like、Mod、And、Or、Xor、Not、\<\<, >>...

オーバーロードの対象となる演算子のみ宣言できます。 次の表に宣言可能な演算子を示します。

|種類|演算子|
|----------|---------------|
|単項|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|
|2 項|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|
|変換 (単項)|`CType`|

 2 項の一覧に示した `=` 演算子は比較演算子であり、代入演算子ではありません。

 **エラー ID:** BC33000

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 演算子をオーバーロード可能な演算子の中から選択します。

- 直接オーバーロードできない演算子をオーバーロードする機能が必要な場合は、適切なパラメーターを受け取り適切な値を返す `Function` プロシージャを作成します。

## <a name="see-also"></a>関連項目

- [Operator ステートメント](../statements/operator-statement.md)
- [演算子プロシージャ](../../programming-guide/language-features/procedures/operator-procedures.md)
- [方法: 演算子を定義する](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [方法: 変換演算子を定義する](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Function ステートメント](../statements/function-statement.md)
