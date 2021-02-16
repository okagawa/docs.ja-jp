---
description: '詳細情報: 方法:Visual Basic で XML ドキュメントを作成する'
title: '方法: XML ドキュメントを作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: d54c79d820a170b246e5c85d7562487fbe66f39c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475956"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>方法: Visual Basic で XML ドキュメントを作成する

この例では、XML ドキュメント コメントをコードに追加する方法を示します。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-xml-documentation-for-a-type-or-member"></a>型またはメンバーの XML ドキュメントを作成するには

1. **コード エディター** で、ドキュメントを作成する型またはメンバーの上の行にカーソルを置きます。

2. `'''` (3 つの単一引用符) を入力します。

    型またはメンバーの XML スケルトンが **コード エディター** に追加されます。

3. 適切なタグの間に説明情報を追加します。

    > [!NOTE]
    > XML ドキュメント ブロック内に行を追加する場合は、各行が `'''` で始まる必要があります。

4. 新しい XML ドキュメント コメントと共に型またはメンバーを使用するコードを追加します。

    IntelliSense により、型またはメンバーの \<summary> タグのテキストが表示されます。

5. コードをコンパイルして、ドキュメント コメントを含む XML ファイルを生成します。 詳細については、「[-doc](../../reference/command-line-compiler/doc.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [XML の使用によるコードのドキュメントの作成](documenting-your-code-with-xml.md)
- [XML のコメント用タグ](../../language-reference/xmldoc/index.md)
- [-doc](../../reference/command-line-compiler/doc.md)
