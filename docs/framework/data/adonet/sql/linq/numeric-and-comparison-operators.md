---
description: '詳細情報: 数値演算子および比較演算子'
title: 数値演算子および比較演算子
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 5b17f19769436ac4e575ac974668eadc3b17b8f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695529"
---
# <a name="numeric-and-comparison-operators"></a>数値演算子および比較演算子

算術演算子と比較演算子は、次の点を除いて、共通言語ランタイム (CLR) では期待どおりに動作します。

- SQL では、浮動小数点数に対して剰余演算子がサポートされません。

- SQL ではチェックされない算術はサポートされません。

- インクリメント演算子とデクリメント演算子は、SQL に複製できない式で使用すると副作用があるため、SQL ではサポートされません。

## <a name="supported-operators"></a>サポートされる演算子

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、次の演算子をサポートしています。

- 基本算術演算子

  - `+`

  - `-` (減算)

  - `*`

  - `/`

  - Visual Basic 整数除算 (`\`)

  - `%` (Visual Basic `Mod`)

  - `<<`

  - `>>`

  - `-` (単項マイナス符号)

- 基本比較演算子

  - Visual Basic `=` および C# `==`

  - Visual Basic `<>` および C# `!=`

  - Visual Basic `Is/IsNot`

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a>関連項目

- [データ型と関数](data-types-and-functions.md)
- [C# 演算子](../../../../../csharp/language-reference/operators/index.md)
- [演算子](../../../../../visual-basic/language-reference/operators/index.md)
