---
description: '詳細情報: 方法:プロパティに値を格納する (Visual Basic)'
title: '方法: プロパティに値を格納する'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: 62f5552f821fb98bd3a4695505aba5ff73b08fc7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476203"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>方法: プロパティに値を格納する (Visual Basic)

プロパティに値を格納するには、代入ステートメントの左辺にプロパティ名を指定します。  
  
 プロパティの `Set` プロシージャによって値が格納されますが、名前で明示的に呼び出すことはありません。 変数を使用する場合と同様に、プロパティを使用します。 Visual Basic によってプロパティのプロシージャが呼び出されます。  
  
### <a name="to-store-a-value-in-a-property"></a>プロパティに値を格納するには  
  
1. 代入ステートメントの左辺にプロパティ名を使用します。  
  
     次の例では、`Set` プロシージャを暗黙的に呼び出して、Visual Basic の `TimeOfDay` プロパティの値を正午に設定します。  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. プロパティが引数を受け取る場合は、プロパティ名の後にかっこで囲んだ引数リストを指定します。 引数がない場合は、必要に応じてかっこを省略できます。  
  
3. 引数リストの引数をコンマで区切ってかっこ内に配置します。 プロパティで定義されている対応するパラメーターと同じ順序で引数を指定してください。  
  
4. 代入ステートメントの右辺で生成された値がプロパティに格納されます。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [Property プロシージャ](./property-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Property ステートメント](../../../language-reference/statements/property-statement.md)
- [Visual Basic のプロパティと変数の違い](./differences-between-properties-and-variables.md)
- [方法: プロパティを作成する](./how-to-create-a-property.md)
- [方法: 複数のアクセス レベルを持つプロパティを宣言する](./how-to-declare-a-property-with-mixed-access-levels.md)
- [方法: プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)
- [方法: 既定のプロパティを宣言して呼び出す (Visual Basic)](./how-to-declare-and-call-a-default-property.md)
- [方法: プロパティから値を取得する](./how-to-get-a-value-from-a-property.md)
