---
description: '詳細情報: <inheritdoc> (C# プログラミング ガイド)'
title: <inheritdoc> - C# プログラミング ガイド
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 960bdfbcec1e3f6a89675273f63b6d398e44947e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719397"
---
# <a name="inheritdoc-c-programming-guide"></a>\<inheritdoc> (C# プログラミング ガイド)

## <a name="syntax"></a>構文  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a>InheritDoc

基底クラス、インターフェイス、および同様のメソッドから、XML コメントを継承します。 これにより、重複する XML コメントの不要なコピーと貼り付けを行う必要がなくなり、XML コメントが自動的に同期されたままになります。
  
## <a name="remarks"></a>解説  

基底クラスまたはインターフェイスに XML コメントを追加し、InheritDoc によってそのコメントが実装するクラスにコピーされるようにします。

同期メソッドに XML コメントを追加し、InheritDoc によってそのコメントが同じメソッドの非同期バージョンにコピーされるようにします。  

特定のメンバーからコメントをコピーしたい場合は、`cref` 属性を使用してそのメンバーを指定できます。
  
## <a name="examples"></a>例

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ドキュメント コメントとして推奨されるタグ](./recommended-tags-for-documentation-comments.md)
