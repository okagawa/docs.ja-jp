---
title: "'<functionname>' は宣言されていません (スマート デバイスおよび Visual Basic コンパイラ エラー)"
ms.date: 07/20/2015
f1_keywords:
- bc30766
- vbc30766
helpviewer_keywords:
- BC30766
ms.assetid: 13918600-6087-40d7-8134-32aa9d3bfda4
ms.openlocfilehash: 1c57e1aaea2eb52133d37b782f8fa0ddd96943a9
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163403"
---
# <a name="bc30766-functionname-is-not-declared-smart-devicevisual-basic-compiler-error"></a>BC30766: '\<functionname>' は宣言されていません (スマート デバイスおよび Visual Basic コンパイラ エラー)

<`functionname`> が宣言されていません。 通常、ファイル I/O 機能は `Microsoft.VisualBasic` 名前空間で使用できますが、.NET Compact Framework のターゲット バージョンではサポートされていません。

 **エラー ID:** BC30766

## <a name="to-correct-this-error"></a>このエラーを解決するには

- `System.IO` 名前空間で定義された関数を使用して、ファイル操作を実行します。

## <a name="see-also"></a>関連項目

- <xref:System.IO>
- [Visual Basic におけるファイル アクセス](../../developing-apps/programming/drives-directories-files/file-access.md)
