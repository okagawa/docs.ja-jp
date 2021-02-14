---
description: '詳細情報: BC33000:演算子宣言は次のいずれかでなければなりません: +、-、*、,/、^、&amp;、Like、Mod、And、Or、Xor、Not、<<、>>...'
title: '演算子宣言は次のいずれかでなければなりません: +、-、*、\、/、^、&amp;、Like、Mod、And、Or、Xor、Not、<<、>>、=、<>、<、<=、>、>=、CType、IsTrue、または IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: 0ad82a6414387278622a10624952ebc35e7e9b83
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795561"
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
