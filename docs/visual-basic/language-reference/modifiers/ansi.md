---
description: '詳細情報: Ansi (Visual Basic)'
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: c93472cbf6a8203f05353e0394b52c44686c0070
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701197"
---
# <a name="ansi-visual-basic"></a>Ansi (Visual Basic)

Visual Basic では、宣言する外部プロシージャの名前に関係なく、すべての文字列を米国規格協会 (ANSI) 値にマーシャリングする必要があることを指定します。  
  
 プロジェクトの外部で定義されたプロシージャを呼び出すと、Visual Basic コンパイラが、プロシージャを正しく呼び出すために必要な情報にアクセスできません。 この情報には、プロシージャの配置場所、識別方法、呼び出しシーケンスと戻り値の型、および使用される文字列の文字セットが含まれます。 [Declare ステートメント](../statements/declare-statement.md)は、外部プロシージャへの参照を作成し、この必要な情報を提供します。  
  
 `Declare` ステートメントの `charsetmodifier` 部分では、外部プロシージャの呼び出し時に、文字列をマーシャリングするための文字セット情報を指定します。 また、Visual Basic が外部ファイルで外部プロシージャ名を検索する方法にも影響します。 `Ansi` 修飾子は、Visual Basic がすべての文字列を ANSI 値にマーシャリングする必要があり、検索時に名前を変更せずにプロシージャを検索する必要があることを指定します。  
  
 文字セット修飾子が指定されていない場合は、`Ansi` が既定値になります。  
  
## <a name="remarks"></a>Remarks  

 `Ansi` 修飾子は、次のコンテキストで使用できます。  
  
 [Declare ステートメント](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>スマート デバイス開発者向けのメモ  

 このキーワードはサポートされていません。  
  
## <a name="see-also"></a>関連項目

- [Auto](auto.md)
- [Unicode](unicode.md)
- [キーワード](../keywords/index.md)
