---
title: 型 'type1' の値を 'type2' に変換できません
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 107936aa969690d0cc9fd4a2605cfceea31eeca8
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161414"
---
# <a name="bc31194-value-of-type-type1-cannot-be-converted-to-type2"></a>BC31194:型 'type1' の値を 'type2' に変換できません

型 'type1' の値を 'type2' に変換できません。 '\<parentElement>' の最初の要素の文字列値は、'Value' プロパティを使用して取得できます。

 XML リテラルを特定の型を暗黙的にキャストしようとしました。 XML リテラルは、指定した型に暗黙的にキャストできません。

 **エラー ID:** BC31194

## <a name="to-correct-this-error"></a>このエラーを解決するには

- XML リテラルの `Value` プロパティを使用して、その値を `String`として参照します。 `CType` 関数、別の型変換関数、または <xref:System.Convert> クラスを使用して、指定した型として値をキャストします。

## <a name="see-also"></a>関連項目

- <xref:System.Convert>
- [データ型変換関数](../functions/type-conversion-functions.md)
- [XML リテラル](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
