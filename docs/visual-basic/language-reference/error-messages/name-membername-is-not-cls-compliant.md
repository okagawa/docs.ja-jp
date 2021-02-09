---
description: '詳細情報: BC40031:名前 <membername> は CLS に準拠していません。'
title: 名前 <membername> は CLS に準拠していません。
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 7abc4aee8bb468b523e5bdd2ac13947d19c926bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795756"
---
# <a name="bc40031-name-membername-is-not-cls-compliant"></a>BC40031:名前 \<membername> は CLS に準拠していません。

アセンブリが `<CLSCompliant(True)>` としてマークされているのに、アンダースコア (`_`) で始まる名前のメンバーを公開しています。

 プログラミング要素には 1 つ以上のアンダースコアを含めることができますが、[言語への非依存性、および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md) (CLS) に準拠するためには、先頭をアンダースコアにしてはなりません。 「 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。

 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。 このパラメーターには既定値がありません。値を指定する必要があります。

 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。

 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。

 **エラー ID:** BC40031

## <a name="to-correct-this-error"></a>このエラーを解決するには

- ソース コードを制御できる場合は、アンダースコアで始まらないようにメンバー名を変更します。

- メンバーの名前が変更されないようにする必要がある場合は、その定義から <xref:System.CLSCompliantAttribute> を削除するか、`<CLSCompliant(False)>` としてマークします。 アセンブリを `<CLSCompliant(True)>` としてマークすることもできます。

## <a name="see-also"></a>関連項目

- [宣言された要素の名前](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [Visual Basic の名前付け規則](../../programming-guide/program-structure/naming-conventions.md)
