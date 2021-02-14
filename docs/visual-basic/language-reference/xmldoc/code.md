---
description: '詳細情報: <code> (Visual Basic)'
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 80fc0988f60d9d82b9c88734f86b20ebccc80b7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787501"
---
# <a name="code-visual-basic"></a>\<code> (Visual Basic)

テキストが複数コード行であることを示します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a>パラメーター  

 `content`  
 コードとしてマークするテキスト。  
  
## <a name="remarks"></a>Remarks  

 `<code>` タグを使用して、複数行をコードとして指定します。 説明内のテキストをコードとしてマークする場合は、[\<c>](c.md) を使用します。  
  
 コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  

 この例では、\<code> タグを使用して、`ID` フィールドを使用するためのコード例を追加します。  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](index.md)
