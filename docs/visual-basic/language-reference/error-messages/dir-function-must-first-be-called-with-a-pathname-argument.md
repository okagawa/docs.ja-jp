---
description: "詳細情報: 'Dir' 関数は、'Pathname' 引数で最初に呼び出されなければなりません。"
title: "'Dir' 関数は、'Pathname' 引数で最初に呼び出されなければなりません。"
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 076828978b27911a97a4767cde1b1d7b04317a31
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479973"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>'Dir' 関数は、'Pathname' 引数で最初に呼び出されなければなりません。

`Dir` 関数の最初の呼び出しには、`PathName` 引数は含まれていません。 `Dir` の最初の呼び出しには `PathName` を含める必要がありますが、後続の `Dir` の呼び出しには、次の項目を取得するためのパラメーターを含める必要はありません。

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 関数呼び出しに `PathName` 引数を指定します。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
