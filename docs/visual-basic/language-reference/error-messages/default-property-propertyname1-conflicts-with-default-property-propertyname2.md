---
title: 既定プロパティ '<propertyname1>' は、'<propertyname2>' の既定プロパティ '<classname>' と競合しているため、'Shadows' と宣言できません。
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 290971a3173c59f08fbd279b6fffe3bcb618cb72
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160608"
---
# <a name="bc40007-default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a>BC40007:既定プロパティ '\<propertyname1>' は、'\<propertyname2>' の既定プロパティ '\<classname>' と競合しているため、'Shadows' と宣言できません。

プロパティが、基底クラスで定義されたプロパティと同じ名前で宣言されています。 この場合、このクラスのプロパティは、基底クラス プロパティをシャドウする必要があります。

 このメッセージは警告です。 `Shadows` は、既定で指定されていると見なされます。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。

 **エラー ID:** BC40007

## <a name="to-correct-this-error"></a>このエラーを解決するには

- `Shadows` キーワードを宣言に追加するか、宣言されるプロパティの名前を変更します。

## <a name="see-also"></a>関連項目

- [Shadows](../modifiers/shadows.md)
- [Visual Basic におけるシャドウ](../../programming-guide/language-features/declared-elements/shadowing.md)
