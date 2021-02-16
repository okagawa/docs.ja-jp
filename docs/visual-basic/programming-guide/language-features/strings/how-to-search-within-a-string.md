---
description: '詳細情報: 方法 : 文字列内を検索する (Visual Basic)'
title: '方法: 文字列内を検索する'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: dab9faf91eef2e6d845805693227e1a6735ec796
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429729"
---
# <a name="how-to-search-within-a-string-visual-basic"></a>方法 : 文字列内を検索する (Visual Basic)

この記事では、Visual Basic で文字列内を検索する方法の例を示します。

## <a name="example"></a>例

この例では、<xref:System.String> オブジェクトに対して <xref:System.String.IndexOf%2A> メソッドを呼び出して、部分文字列が最初に出現した位置のインデックスを報告します。

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a>信頼性の高いプログラミング

<xref:System.String.IndexOf%2A> メソッドは、最初に出現した部分文字列の最初の文字の位置を返します。 インデックスは 0 から始まります。つまり、文字列の最初の文字のインデックスは 0 になります。

<xref:System.String.IndexOf%2A> は、部分文字列が見つからない場合、-1 を返します。

<xref:System.String.IndexOf%2A> メソッドでは大文字と小文字が区別され、現在のカルチャが使用されます。

最適なエラー制御を実現するために、[Try...Catch...Finally ステートメント](../../../language-reference/statements/try-catch-finally-statement.md)構成の `Try` ブロックで文字列検索を囲むことができます。

## <a name="see-also"></a>関連項目

- <xref:System.String.IndexOf%2A>
- [Try...Catch...Finally ステートメント](../../../language-reference/statements/try-catch-finally-statement.md)
- [Visual Basic の文字列の概要](introduction-to-strings.md)
- [文字列](index.md)
