---
description: "詳細情報: BC30617:'Module' ステートメントは、ファイルまたは名前空間レベルでのみ発生します。"
title: "'Module' ステートメントは、ファイルまたは名前空間レベルでのみ発生します。"
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: f5c3ea0cd1c08fb0243043ae50e707e2c59b00f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795782"
---
# <a name="bc30617-module-statements-can-occur-only-at-file-or-namespace-level"></a>BC30617:'Module' ステートメントは、ファイルまたは名前空間レベルでのみ発生します。

`Module` ステートメントは、ソース ファイルの先頭の、`Option` および `Imports` ステートメント、グローバル属性、および名前空間宣言の直後、ただし他のすべての宣言の前に記述する必要があります。

 **エラー ID:** BC30617

## <a name="to-correct-this-error"></a>このエラーを解決するには

- `Module` ステートメントを名前空間の宣言またはソース ファイルの先頭に移動します。

## <a name="see-also"></a>関連項目

- [Module ステートメント](../statements/module-statement.md)
