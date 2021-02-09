---
description: '詳細情報: BC30801:数字を指定するラベルの後には、コロンが必要です。'
title: 数字を指定するラベルの後には、コロンが必要です。
ms.date: 07/20/2015
f1_keywords:
- vbc30801
- bc30801
helpviewer_keywords:
- BC30801
ms.assetid: 67743319-2d1c-496e-bfd9-22b046b43b5a
ms.openlocfilehash: 4c179cc6b74f323c330b093af988f33173e901fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795964"
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
