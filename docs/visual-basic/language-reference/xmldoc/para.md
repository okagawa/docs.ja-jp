---
description: 詳細については、以下をご覧ください。 <para> (Visual Basic)
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 51dd9ff300d980b4c0576566cad5d17375889ba1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740770"
---
# <a name="para-visual-basic"></a>\<para> (Visual Basic)

コンテンツが段落として書式設定されることを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a>パラメーター  

 `content`  
 段落のテキストです。  
  
## <a name="remarks"></a>Remarks  

 `<para>` タグは、[\<summary>](summary.md)、[\<remarks>](remarks.md)、または [\<returns>](returns.md) などのタグ内で使用します。このタグを使用すると、テキストに構造を追加することができます。  
  
 コンパイル時に [-doc](../../reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  

 この例では、`<para>` タグを使用して、`UpdateRecord` メソッドの解説セクションを 2 つの段落に分割します。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](index.md)
