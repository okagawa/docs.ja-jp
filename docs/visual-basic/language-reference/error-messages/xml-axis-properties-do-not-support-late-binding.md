---
description: '詳細情報: BC31168:XML 軸のプロパティは遅延バインディングをサポートしていません'
title: XML 軸のプロパティは遅延バインディングをサポートしていません
ms.date: 07/20/2015
f1_keywords:
- bc31168
- vbc31168
helpviewer_keywords:
- BC31168
ms.assetid: 45707363-55e4-4151-892d-d8729106355b
ms.openlocfilehash: 19fe5bae200eaad9086626421d013bbbf8d143c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640837"
---
# <a name="bc31168-xml-axis-properties-do-not-support-late-binding"></a>BC31168:XML 軸のプロパティは遅延バインディングをサポートしていません

型指定されていないオブジェクトに対して、XML 軸プロパティが参照されています。

 **エラー ID:** BC31168

## <a name="to-correct-this-error"></a>このエラーを解決するには

- XML 軸プロパティを参照する前に、オブジェクトが厳密に型指定された <xref:System.Xml.Linq.XElement> オブジェクトであることを確認してください。

## <a name="see-also"></a>関連項目

- [XML 軸プロパティ](../xml-axis/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
