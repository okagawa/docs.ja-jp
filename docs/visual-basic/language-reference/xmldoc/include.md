---
description: 詳細については、以下をご覧ください。 <include> (Visual Basic)
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 8207b74ed74bd529f2da865777e287320b23d293
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787462"
---
# <a name="include-visual-basic"></a>\<include> (Visual Basic)

ソース コード内の型とメンバーを記述する別のファイルを参照します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a>パラメーター  

 `filename`  
 必須です。 文書を含むファイルの名前。 ファイル名をパスで修飾することができます。 `filename` は二重引用符 (" ") で囲みます。  
  
 `tagpath`  
 必須です。 タグ `name` につながる `filename` 内のタグのパス。 パスは二重引用符 (" ") で囲みます。  
  
 `name`  
 必須です。 コメントの前に配置するタグの名前指定子。 `Name` には `id` が指定されます。  
  
 `id`  
 必須です。 コメントの前に配置するタグの ID。 ID は単一引用符 (' ') で囲みます。  
  
## <a name="remarks"></a>Remarks  

 `<include>` タグを使用して、ソース コード内の型とメンバーを記述する別のファイル内のコメントを参照します。 これは文書化のコメントをソース コード ファイル内に直接配置する方法の代替です。  
  
 `<include>` タグでは、W3C XML Path Language (XPath) Version 1.0 勧告が使用されています。 `<include>` の使用をカスタマイズする方法の詳細については、「<https://www.w3.org/TR/xpath>」を参照してください。  
  
## <a name="example"></a>例  

 この例では、`<include>` タグを使用して、`commentFile.xml` というファイルからメンバー ドキュメント コメントをインポートします。  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 `commentFile.xml` の形式を次に示します。  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](index.md)
