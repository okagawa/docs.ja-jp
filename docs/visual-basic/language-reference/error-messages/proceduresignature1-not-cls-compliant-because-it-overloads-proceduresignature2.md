---
description: '詳細情報: BC40035: <proceduresignature1> は、配列パラメーター型の配列または配列パラメーター型のランクのみが異なる <proceduresignature2> をオーバーロードするため、CLS に準拠していません。'
title: <proceduresignature1> は、配列パラメーター型の配列または配列パラメーター型のランクのみが異なる <proceduresignature2> をオーバーロードするため、CLS に準拠していません。
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 056683033a4eacdc6ad783f5056b639e849e3507
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795392"
---
# <a name="bc40035-proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>BC40035: \<proceduresignature1> は、配列パラメーター型の配列または配列パラメーター型のランクのみが異なる \<proceduresignature2> をオーバーロードするため、CLS に準拠していません。

プロシージャまたはプロパティが別のプロシージャまたはプロパティをオーバーライドする場合、そのプロシージャまたはプロパティは `<CLSCompliant(True)>` としてマークされます。それらのパラメーター リスト間の唯一の違いは、ジャグ配列または配列のランクの入れ子レベルです。

 次の宣言では、2 番目と 3 番目の宣言によってこのエラーが生成されます。

 `Overloads Sub ProcessArray(arrayParam() As Integer)`

 `Overloads Sub ProcessArray(arrayParam()() As Integer)`

 `Overloads Sub ProcessArray(arrayParam(,) As Integer)`

 2 番目の宣言では、元の 1 次元パラメーター `arrayParam` を配列の配列に変更します。 3 番目の宣言は、`arrayParam` を 2 次元配列 (ランク 2) に変更します。 Visual Basic では、これらの変更のいずれかによってのみオーバーロードが異なることが許可されますが、そのようなオーバーロードは、[言語への非依存性、および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md) (CLS) に準拠していません。

 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。 このパラメーターには既定値がありません。値を指定する必要があります。

 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。

 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。

 **エラー ID:** BC40035

## <a name="to-correct-this-error"></a>このエラーを解決するには

- CLS 準拠が必要な場合は、このヘルプ ページで言及されている変更だけよりも多くの点で、相互に異なるようにオーバーロードを定義します。
- このヘルプ ページで言及されている変更によってのみオーバーロードが異なるようにする必要がある場合は、それらの定義から <xref:System.CLSCompliantAttribute> を削除するか、それらを `<CLSCompliant(False)>` とマークします。

## <a name="see-also"></a>関連項目

- [プロシージャのオーバーロード](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [Overloads](../modifiers/overloads.md)
