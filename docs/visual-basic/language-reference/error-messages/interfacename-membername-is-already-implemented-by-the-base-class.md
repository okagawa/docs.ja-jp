---
title: <interfacename>.<membername>' は、基本クラス '<baseclassname>' によって既に実装されています。 <type> の再実装と見なされます。
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 8137f6b1712b6a0752a991f5a3d598b5f958252c
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162818"
---
# <a name="bc42015-interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a>BC42015: \<interfacename>.\<membername>' は、基本クラス '\<baseclassname>' によって既に実装されています。 \<type> の再実装と見なされます。

派生クラスのプロパティ、プロシージャ、またはイベントで `Implements` 句を使用し、基底クラスに既に実装されている派生インターフェイス メンバーを指定します。

 派生クラスでは、その基底クラスによって実装されているインターフェイス メンバーを再実装できます。 このことは、基底クラスの実装をオーバーライドすることとは異なります。 詳細については、「 [Implements](../statements/implements-clause.md)」を参照してください。

 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。

 **エラー ID:** BC42015

## <a name="to-correct-this-error"></a>このエラーを解決するには

- インターフェイス メンバーを再実装する場合は、操作を行う必要はありません。 派生クラスのコードでは、`MyBase` キーワードを使用して基底クラスの実装にアクセスしない限り、再実装されたメンバーにアクセスします。

- インターフェイス メンバーを再実装しない場合は、プロパティ、プロシージャ、またはイベント宣言から、 `Implements` 句を削除します。

## <a name="see-also"></a>関連項目

- [インターフェイス](../../programming-guide/language-features/interfaces/index.md)
