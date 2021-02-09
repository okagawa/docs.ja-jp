---
description: '詳細情報: REM ステートメント (Visual Basic)'
title: REM ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: c82621db98dc66060ae098ee6537ee58b24046a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741316"
---
# <a name="rem-statement-visual-basic"></a>REM ステートメント (Visual Basic)

プログラムのソース コード内に説明のための注記を含めるために使用されます。  
  
## <a name="syntax"></a>構文  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a>指定項目  

 `comment`  
 任意。 含めるコメントのテキストです。 `REM` キーワードと `comment` の間にはスペースが必要です。  
  
## <a name="remarks"></a>Remarks  

 `REM` ステートメントを 1 行に単独で配置することも、別のステートメントの後の行に配置することもできます。 `REM` ステートメントは行の最後のステートメントである必要があります。 別のステートメントの後に続く場合、`REM` は、そのステートメントとスペースで区切る必要があります。  
  
 `REM` ではなく、単一引用符 (`'`) を使用できます。 これは、コメントが同じ行で別のステートメントの後に続くか 1 つの行に単独で存在するかにかかわらず当てはまります。  
  
> [!NOTE]
> 行連結シーケンス (`_`) を使用して `REM` ステートメントを継続することはできません。 コメントが開始された後、コンパイラは、文字に特別な意味があるかどうかを調べません。 複数行のコメントでは、各行で別の `REM` ステートメントまたはコメント記号 (`'`) を使用してください。  
  
## <a name="example"></a>例  

 次の例では、プログラム内に説明のための注記を含めるために使用される `REM` ステートメントを示しています。 また、`REM` ではなく単一引用符文字 (`'`) を使用する別の方法も示しています。  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [コード内のコメント](../../programming-guide/program-structure/comments-in-code.md)
- [方法: コード内でステートメントを分割および連結する](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
