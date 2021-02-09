---
description: 詳細については、以下をご覧ください。 <example> (Visual Basic)
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 643e06fd24e38123dd2693d671b9ab33da5b413e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787488"
---
# <a name="example-visual-basic"></a>\<example> (Visual Basic)

メンバーの例を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a>パラメーター  

 `description`  
 コード例の説明です。  
  
## <a name="remarks"></a>Remarks  

 `<example>` タグを使用すると、メソッドまたは他のライブラリ メンバーの使用例を指定できます。 一般的に、[\<code>](code.md) タグが使用されます。  
  
 コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  

 この例では、`<example>` タグを使用して、`ID` フィールドを使用する例を組み込みます。  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](index.md)
