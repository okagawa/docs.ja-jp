---
description: "詳細情報: BC30766: '<functionname>' は宣言されていません (スマート デバイスおよび Visual Basic コンパイラ エラー)"
title: "'<functionname>' は宣言されていません (スマート デバイスおよび Visual Basic コンパイラ エラー)"
ms.date: 07/20/2015
f1_keywords:
- bc30766
- vbc30766
helpviewer_keywords:
- BC30766
ms.assetid: 13918600-6087-40d7-8134-32aa9d3bfda4
ms.openlocfilehash: 939af146656bc5e5e84b3f0672c730f6a816c043
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796159"
---
# <a name="bc30766-functionname-is-not-declared-smart-devicevisual-basic-compiler-error"></a>BC30766: '\<functionname>' は宣言されていません (スマート デバイスおよび Visual Basic コンパイラ エラー)

<`functionname`> が宣言されていません。 通常、ファイル I/O 機能は `Microsoft.VisualBasic` 名前空間で使用できますが、.NET Compact Framework のターゲット バージョンではサポートされていません。

 **エラー ID:** BC30766

## <a name="to-correct-this-error"></a>このエラーを解決するには

- `System.IO` 名前空間で定義された関数を使用して、ファイル操作を実行します。

## <a name="see-also"></a>関連項目

- <xref:System.IO>
- [Visual Basic におけるファイル アクセス](../../developing-apps/programming/drives-directories-files/file-access.md)
