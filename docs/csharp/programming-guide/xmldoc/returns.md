---
title: <returns> - C# プログラミング ガイド
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 7bc950a8d89a3ac2b5c3b7a68e05c7778e97f85c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287234"
---
# <a name="returns-c-programming-guide"></a>\<returns> (C# プログラミング ガイド)

## <a name="syntax"></a>構文

```xml
<returns>description</returns>
```

## <a name="parameters"></a>パラメーター

- `description`

  戻り値の説明。

## <a name="remarks"></a>Remarks

`<returns>` タグは、戻り値を説明するためにメソッドの宣言のコメントで使用する必要があります。

コンパイル時に [-doc](../../language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。

## <a name="example"></a>例

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ドキュメント コメント用の推奨タグ](./recommended-tags-for-documentation-comments.md)
