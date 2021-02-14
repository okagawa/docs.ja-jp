---
description: "詳細情報: BC40007:既定プロパティ '<propertyname1>' は、'<propertyname2>' の既定プロパティ '<classname>' と競合しているため、'Shadows' と宣言できません"
title: 既定プロパティ '<propertyname1>' は、'<propertyname2>' の既定プロパティ '<classname>' と競合しているため、'Shadows' と宣言できません。
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 8ec7e36da18bbf8dda35e1a521d64268d14b7b26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796640"
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
