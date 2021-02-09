---
description: '詳細情報: Visual Basic でサポートされていないオートメーションが変数で使用されています。'
title: サポートされていない Automation の型が変数で使用されています
ms.date: 07/20/2015
f1_keywords:
- vbrID458
ms.assetid: bde4f4da-493b-452c-b6e4-1d370edba4cd
ms.openlocfilehash: 9aa8f8a2a49e54c547dc47d38305d40f855b1815
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666148"
---
# <a name="variable-uses-an-automation-type-not-supported-in-visual-basic"></a>Visual Basic でサポートされていないオートメーションが変数で使用されています。

Visual Basic でサポートされていないデータ型を持つタイプ ライブラリまたはオブジェクト ライブラリに定義された変数を使用しようとしました。

## <a name="to-correct-this-error"></a>このエラーを解決するには

- Visual Basic によって認識される型の変数を使用します。

     \- または -

- `FileGet` または `FileGetObject` の使用中にこのエラーが発生した場合は、使用しようとしているファイルが `FilePut` または `FilePutObject` と共に書き込まれていることを確認してください。

## <a name="see-also"></a>関連項目

- [データの種類](../data-types/index.md)
