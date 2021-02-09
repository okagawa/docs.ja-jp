---
description: '詳細情報: Module <keyword> (Visual Basic)'
title: Module <keyword>
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: 1bd25b00b41f5da4fca535220fe4e1694c81baca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640694"
---
# <a name="module-keyword-visual-basic"></a>Module \<keyword> (Visual Basic)

ソース ファイルの先頭の属性が現在のアセンブリ モジュールに適用されることを指定します。  
  
## <a name="remarks"></a>Remarks  

 個々のプログラミング要素には、クラスやプロパティなどの多くの属性が関連しています。 そのような属性を適用するには、山かっこ (`< >`) 内の属性ブロックを宣言ステートメントに直接アタッチします。  
  
 属性が次の要素だけでなく、現在のアセンブリ モジュールに関連する場合は、属性ブロックをソース ファイルの先頭に配置し、`Module` キーワードで属性を識別します。 それをアセンブリ全体に適用する場合は、[Assembly](assembly.md) キーワードを使用します。  
  
 `Module` 修飾子は、[Module ステートメント](../statements/module-statement.md)と同じではありません。  
  
## <a name="see-also"></a>関連項目

- [Assembly](assembly.md)
- [Module ステートメント](../statements/module-statement.md)
- [属性の概要](../../programming-guide/concepts/attributes/index.md)
