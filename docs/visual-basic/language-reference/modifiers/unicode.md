---
description: '詳細情報: Unicode (Visual Basic)'
title: Unicode
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: b0c71d8fdefe3f0d240201e0d57265e5c6081d50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700716"
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)

Visual Basic では、宣言する外部プロシージャの名前に関係なく、すべての文字列を Unicode 値にマーシャリングする必要があることを示します。  
  
 プロジェクトの外側に定義されたプロシージャを呼び出すと、Visual Basic コンパイラは、プロシージャを正しく呼び出すために必要な情報にアクセスできません。 この情報には、プロシージャの配置場所、識別方法、呼び出し元のシーケンスと戻り値の型、および使用されている文字列の文字セットが含まれます。 [Declare ステートメント](../statements/declare-statement.md)は、外部プロシージャへの参照を作成し、この必要な情報を提供します。  
  
 `Declare` ステートメントの `charsetmodifier` 部分では、外部プロシージャの呼び出し時に文字列をマーシャリングするための文字セット情報を指定します。 これは、Visual Basic が外部ファイルで外部プロシージャ名を検索する方法にも影響します。 `Unicode` 修飾子は、Visual Basic がすべての文字列を Unicode 値にマーシャリングする必要があり、検索時に名前を変更せずにプロシージャを検索する必要があることを指定します。  
  
 文字セット修飾子が指定されていない場合は、`Ansi` が既定値になります。  
  
## <a name="remarks"></a>Remarks  

 `Unicode` 修飾子は、次のコンテキストで使用できます。  
  
 [Declare ステートメント](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>スマート デバイス開発者向けのメモ  

 このキーワードはサポートされていません。  
  
## <a name="see-also"></a>関連項目

- [Ansi](ansi.md)
- [Auto](auto.md)
- [キーワード](../keywords/index.md)
