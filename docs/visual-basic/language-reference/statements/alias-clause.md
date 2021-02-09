---
description: '詳細情報: Alias 句 (Visual Basic)'
title: Alias 句
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: bf0ee1c22105b29aedb99ce45a99ba866f4b93c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674078"
---
# <a name="alias-clause-visual-basic"></a>Alias 句 (Visual Basic)

外部プロシージャがその DLL で別の名前を使用することを示します。  
  
## <a name="remarks"></a>Remarks  

 `Alias` キーワードは次のコンテキストで使用できます。  
  
 [Declare ステートメント](declare-statement.md)  
  
 次の例では、`Alias` キーワードを使用して、advapi32.dll 内の関数の名前 `GetUserNameA` を指定しています。この例では代わりに `getUserName` が使用されています。 関数 `getUserName` はサブ `getUser` で呼び出され、それによって現在のユーザーの名前が表示されます。  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>関連項目

- [キーワード](../keywords/index.md)
