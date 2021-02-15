---
description: 詳細については、「定義クラスのインスタンスではないオブジェクトでフレンド関数を呼び出すことはできません」を参照してください。
title: 定義クラスのインスタンスではないオブジェクトのフレンド関数は呼び出せません
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: 612a169cf976881b82cb0bb0c44ac6c6e7f91755
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100478699"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a>定義クラスのインスタンスではないオブジェクトのフレンド関数は呼び出せません

クラスの `Friend` プロシージャを呼び出そうとするか、プロセス間またはスレッド間で `Friend` プロパティまたはメソッドにアクセスしようとしました。 `Friend` 手順はクラスの外部のモジュールから呼び出せますが、クラスが定義されているプロジェクトの一部です。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- クラスが定義されているプロジェクトの一部であるモジュールからプロシージャを呼び出しているか、またはアクセスしていることを確認します。  
  
## <a name="see-also"></a>関連項目

- [Friend](../language-reference/modifiers/friend.md)
