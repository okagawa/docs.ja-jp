---
description: 詳細については、以下をご覧ください。 <value> (Visual Basic)
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 80a3ef875eea4418d28d60dac1818f3390c361ee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640252"
---
# <a name="value-visual-basic"></a>\<value> (Visual Basic)

プロパティの説明を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>パラメーター  

 `property-description`  
 プロパティの説明。  
  
## <a name="remarks"></a>Remarks  

 `<value>` タグを使用して、プロパティを記述します。 Visual Studio 開発環境では、コード ウィザードを使用してプロパティを追加するときに、新しいプロパティの [\<summary>](summary.md) タグが追加されることにご注意ください。 その後、手動で `<value>` タグを追加してプロパティが表す値を記述する必要があります。  
  
 コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  

 この例では、`<value>` タグを使用して、`Counter` プロパティに保持されている値を記述します。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](index.md)
