---
description: '詳細情報: 方法:Visual Basic でファイル名とパスを検証する'
title: '方法: ファイル名とパスを検証する'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: 02a48ea7cbf3291cb2fe1c64c4e636a273842546
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429741"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>方法: Visual Basic でファイル名とパスを検証する

この例では、文字列がファイル名とパスのどちらを表すかを示す `Boolean` 値が返されます。 この検証では、ファイル システムで許可されていない文字が名前に含まれているかどうかがチェックされます。  
  
## <a name="example"></a>例  

 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 この例では、名前にコロンが正しく配置されていないか、名前のないディレクトリがあるか、または名前の長さがシステム定義の最大長を超えているかどうかはチェックされません。 また、アプリケーションが指定された名前のファイル システム リソースにアクセスするアクセス許可を持っているかどうかもチェックされません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Visual Basic における文字列の検証](validating-strings.md)
