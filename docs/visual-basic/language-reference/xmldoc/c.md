---
description: '詳細情報: <c> (Visual Basic)'
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 350a5dbf2dee2911c356a7c76a9bafbab35fd71e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787514"
---
# <a name="c-visual-basic"></a>\<c> (Visual Basic)

説明内のテキストがコードであることを示します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---|---|  
|`text`|コードとして指定するテキストです。|  
  
## <a name="remarks"></a>Remarks  

 `<c>` タグを使用すると、説明内のテキストをコードとしてマークする必要があることを指定できます。 複数行をコードとして示す場合は、[\<code>](code.md) を使用します。  
  
 コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  

 この例では、summary セクションで `<c>` タグを使用して、`Counter` がコードであることを示します。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](index.md)
