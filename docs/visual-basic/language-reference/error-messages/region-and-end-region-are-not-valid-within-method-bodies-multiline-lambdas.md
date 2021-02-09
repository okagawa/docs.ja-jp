---
description: "詳細情報: BC32025: '#Region' および '#End Region' ステートメントは、メソッド本体や複数行ラムダの内部では有効ではありません"
title: "'#Region' および '#End Region' ステートメントは、メソッド本体や複数行ラムダの内部では有効ではありません。"
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 0746b9caf677699d6fbbf0c5a7063b1b33d86f3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792025"
---
# <a name="bc32025-region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>BC32025: '#Region' および '#End Region' ステートメントは、メソッド本体や複数行ラムダの内部では有効ではありません

`#Region` ブロックは、クラス、モジュール、または名前空間レベルで宣言する必要があります。 折りたたみ可能な領域には 1 つ以上のプロシージャを含めることができますが、プロシージャの内部で開始または終了することはできません。

 **エラー ID:** BC32025

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. 前の手順が `End Function` または `End Sub` ステートメントで適切に終了していることを確認します。

2. `#Region` ディレクティブと `#End Region` ディレクティブが同じコード ブロック内にあることを確認します。

## <a name="see-also"></a>関連項目

- [#Region ディレクティブ](../directives/region-directive.md)
