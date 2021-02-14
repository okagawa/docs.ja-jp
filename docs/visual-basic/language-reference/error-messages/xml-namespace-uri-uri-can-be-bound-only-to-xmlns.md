---
description: "詳細情報: BC31183:XML 名前空間 URI `http://www.w3.org/XML/1998/namespace` は 'xmlns' にのみバインドできます"
title: XML 名前空間 URI '<uri>' は 'xmlns' にのみバインドできます。
ms.date: 07/20/2015
f1_keywords:
- bc31183
- vbc31183
helpviewer_keywords:
- BC31183
ms.assetid: 0ab1dbce-8397-4959-b2cd-f58798b051a0
ms.openlocfilehash: e6a552f4754a12b8e80e5333232d0c48432f7a63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701392"
---
# <a name="bc31183-xml-namespace-uri-httpwwww3orgxml1998namespace-can-be-bound-only-to-xmlns"></a>BC31183:XML 名前空間 URI `http://www.w3.org/XML/1998/namespace` は 'xmlns' にのみバインドできます

URI `http://www.w3.org/XML/1998/namespace` は、XML 名前空間宣言で使用されます。 この URI は予約された名前空間であり、XML 名前空間宣言に含めることはできません。

 **エラー ID:** BC31183

## <a name="to-correct-this-error"></a>このエラーを解決するには

XML 名前空間宣言を削除するか、URI `http://www.w3.org/XML/1998/namespace` を有効な名前空間 URI に置き換えます。

## <a name="see-also"></a>関連項目

- [Imports ステートメント (XML 名前空間)](../statements/imports-statement-xml-namespace.md)
- [XML リテラル](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
