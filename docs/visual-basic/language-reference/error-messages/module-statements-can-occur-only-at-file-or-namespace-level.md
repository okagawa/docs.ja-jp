---
title: "'Module' ステートメントは、ファイルまたは名前空間レベルでのみ発生します。"
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: b946a527d3de3a030ac03691c77afcf440f518ee
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160315"
---
# <a name="bc30617-module-statements-can-occur-only-at-file-or-namespace-level"></a>BC30617:'Module' ステートメントは、ファイルまたは名前空間レベルでのみ発生します。

`Module` ステートメントは、ソース ファイルの先頭の、`Option` および `Imports` ステートメント、グローバル属性、および名前空間宣言の直後、ただし他のすべての宣言の前に記述する必要があります。

 **エラー ID:** BC30617

## <a name="to-correct-this-error"></a>このエラーを解決するには

- `Module` ステートメントを名前空間の宣言またはソース ファイルの先頭に移動します。

## <a name="see-also"></a>関連項目

- [Module ステートメント](../statements/module-statement.md)
