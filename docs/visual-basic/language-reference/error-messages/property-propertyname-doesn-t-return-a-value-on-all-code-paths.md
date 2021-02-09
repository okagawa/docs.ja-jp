---
description: "詳細情報: BC42107:プロパティ '<propertyname>' は、すべてのコードのパスでは値を返しません。"
title: プロパティ '<propertyname>' は、すべてのコードのパスでは値を返しません。
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 9aa0d6fea1feeaf7503f5f8831fbd3de910a4822
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774890"
---
# <a name="bc42107-property-propertyname-doesnt-return-a-value-on-all-code-paths"></a>BC42107:プロパティ '\<propertyname>' は、すべてのコードのパスでは値を返しません。

プロパティ '\<propertyname>' は、すべてのコードのパスでは値を返しません。 この結果が使用されると、実行時に Null 参照例外が生じる可能性があります。

プロパティ `Get` プロシージャのコードには、値を返さないパスが少なくとも 1 つ含まれています。

 次のいずれかの方法で、プロパティ `Get` プロシージャから値を返すことができます。

- プロパティ名に値を代入して、`Exit Property` ステートメントを実行します。

- プロパティ名に値を代入して、`End Get` ステートメントを実行します。

- [return ステートメント](../statements/return-statement.md)に値を含めます。

制御が `Exit Property` または `End Get` に渡され、プロパティ名に何も値を代入していない場合、`Get` プロシージャでは、プロパティのデータ型の既定値が返されます。 詳細については、「[Function ステートメント](../statements/function-statement.md)」の "動作" に関する記述を参照してください。

既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。

**エラー ID:** BC42107

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 制御フロー ロジックをチェックし、戻り値を返すすべてのステートメントの前に値を代入してください。

  常に `Return` ステートメントを使用すれば、プロシージャからのすべての戻り値で、値が返されることを簡単に保証できます。 これを実行する場合、`End Get` の前の最後のステートメントは、`Return` ステートメントでなければなりません。

## <a name="see-also"></a>関連項目

- [Property プロシージャ](../../programming-guide/language-features/procedures/property-procedures.md)
- [Property ステートメント](../statements/property-statement.md)
- [Get ステートメント](../statements/get-statement.md)
