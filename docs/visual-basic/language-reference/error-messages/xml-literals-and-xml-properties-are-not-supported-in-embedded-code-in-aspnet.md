---
description: '詳細情報: BC31200:XML リテラルおよび XML プロパティは、ASP.NET 内の埋め込みコードではサポートされません'
title: XML リテラルおよび XML プロパティは、ASP.NET 内の埋め込みコードではサポートされません
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 0a5328676ee38a56334b77f665a464daa586ce3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701405"
---
# <a name="bc31200-xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a>BC31200:XML リテラルおよび XML プロパティは、ASP.NET 内の埋め込みコードではサポートされません

XML リテラルおよび XML プロパティは、ASP.NET 内の埋め込みコードではサポートされません。 XML 機能を使用するには、コードをコードビハインドに移動します。

 XML リテラルまたは XML 軸プロパティは、ASP.NET ファイルの埋め込みコード (`<%= =>`) 内で定義されます。

 **エラー ID:** BC31200

## <a name="to-correct-this-error"></a>このエラーを解決するには

- XML リテラルまたは XML 軸プロパティが含まれているコードを、ASP.NET 分離コード ファイルに移動します。

## <a name="see-also"></a>関連項目

- [XML リテラル](../xml-literals/index.md)
- [XML 軸プロパティ](../xml-axis/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
