---
title: 数字を指定するラベルの後には、コロンが必要です。
ms.date: 07/20/2015
f1_keywords:
- vbc30801
- bc30801
helpviewer_keywords:
- BC30801
ms.assetid: 67743319-2d1c-496e-bfd9-22b046b43b5a
ms.openlocfilehash: 6b89f23731e75b5248390d02e3c05410104bde6b
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163312"
---
# <a name="bc30801-labels-that-are-numbers-must-be-followed-by-colons"></a>BC30801:数字を指定するラベルの後には、コロンが必要です。

行番号は、他の種類のラベルと同じ規則に従い、コロンが含まれている必要があります。

 **エラー ID:** BC30801

## <a name="to-correct-this-error"></a>このエラーを解決するには

- コード行の先頭に、番号とその後にコロンを置きます。たとえば、次のようにします。

    ```vb
    400:    X += 1
    ```

## <a name="see-also"></a>関連項目

- [GoTo ステートメント](../statements/goto-statement.md)
