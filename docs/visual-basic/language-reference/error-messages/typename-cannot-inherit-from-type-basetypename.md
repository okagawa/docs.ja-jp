---
description: "詳細情報: BC30910: ベース <type> のアクセスをアセンブリの外側に展開しているため、'<typename>' は <type> '<basetypename>' から継承できません"
title: ベース <typename> のアクセスをアセンブリの外側に展開しているため、'<type>' は <basetypename> '<type>' から継承できません。
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 332bfcbe9345f03605d6e1d6ded4a3e931ed491f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641097"
---
# <a name="bc30910-typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>BC30910: ベース \<type> のアクセスをアセンブリの外側に展開しているため、'\<typename>' は \<type> '\<basetypename>' から継承できません

クラスまたはインターフェイスは、基底クラスまたはインターフェイスから継承されますが、アクセス レベルの制限が緩くなります。

 たとえば、`Public` インターフェイスは `Friend` インターフェイスから継承し、または `Protected` クラスは、`Private` クラスから継承します。 これにより、目的のレベルを超えてアクセスする基底クラスまたはインターフェイスが公開されます。

 **エラー ID:** BC30910

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 派生クラスまたはインターフェイスのアクセス レベルを、少なくとも基底クラスまたはインターフェイスのアクセス レベルの制限になるように変更します。

     \- または -

- 制限の緩いアクセス レベルが必要な場合は、`Inherits` ステートメントを削除します。 より制限の厳しい基底クラスまたはインターフェイスから継承することはできません。

## <a name="see-also"></a>関連項目

- [Class ステートメント](../statements/class-statement.md)
- [Interface ステートメント](../statements/interface-statement.md)
- [Inherits ステートメント](../statements/inherits-statement.md)
- [Visual Basic でのアクセス レベル](../../programming-guide/language-features/declared-elements/access-levels.md)
