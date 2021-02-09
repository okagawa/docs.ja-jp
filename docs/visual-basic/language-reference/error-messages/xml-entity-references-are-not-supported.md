---
description: '詳細情報: BC31180:XML エンティティの参照はサポートされていません'
title: XML エンティティの参照はサポートされていません
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: c45202fbd97d2343caf6bf4cdccf9368d0a7a295
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701418"
---
# <a name="bc31180-xml-entity-references-are-not-supported"></a>BC31180:XML エンティティの参照はサポートされていません

XML 1.0 仕様で定義されていないエンティティ参照 (`©` など) が、XML リテラルの値として含まれています。 XML リテラルでは、`&`、`"`、`<`、`>`、および `'` の XML エンティティ参照のみがサポートされています。

 **エラー ID:** BC31180

## <a name="to-correct-this-error"></a>このエラーを解決するには

- サポートされていないエンティティ参照を削除します。

## <a name="see-also"></a>関連項目

- [XML リテラルと XML 1.0 仕様](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [XML リテラル](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
