---
description: 詳細については、以下をご覧ください。 <summary> (Visual Basic)
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 4d4b1ecf0fa054eb625c1a3cf09c1cab4e661ef2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640291"
---
# <a name="summary-visual-basic"></a>\<summary> (Visual Basic)

メンバーの概要を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a>パラメーター  

 `description`  
 オブジェクトの概要。  
  
## <a name="remarks"></a>Remarks  

 `<summary>` タグを使用して、型または型メンバーを記述します。 型の説明に補足情報を追加するには、[\<remarks>](remarks.md) を使用します。  
  
 `<summary>` タグのテキストは、IntelliSense での型に関する唯一のソースで、オブジェクト ブラウザーにも表示されます。 オブジェクト ブラウザーについては、「[コードの構造の表示](/visualstudio/ide/viewing-the-structure-of-code)」を参照してください。  
  
 コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  

 この例では、`<summary>` タグを使用して `ResetCounter` メソッドと `Counter` プロパティを記述します。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](index.md)
