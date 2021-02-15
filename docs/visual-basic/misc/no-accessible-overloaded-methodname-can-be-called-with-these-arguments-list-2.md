---
description: 詳細については、次の情報を参照してください。 <methodname> 縮小変換しないで、これらの引数を指定して呼び出すことができるアクセス可能なオーバーロードされた ' <list>
title: 縮小変換しないで、これらの引数と共に呼び出せるオーバーロードされたアクセス可能な '<methodname>' はありません <list>
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousCall2
ms.assetid: 13b20ffa-9f02-4971-a3cb-e08b402fd971
ms.openlocfilehash: a802b420a01c1894feca2c61c0bfdbb7be5104f5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475709"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-narrowing-conversion-list"></a>縮小変換しないで、これらの引数と共に呼び出せるオーバーロードされたアクセス可能な '\<methodname>' はありません\<list>

オーバーロードされたメソッドが呼び出されましたが、メソッドは縮小変換せずに指定された引数のリストと一致しません。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. `Option Strict Off`を指定します。
  
2. オーバーロードされたメソッドのシグネチャと一致するように、引数を変更します。  
  
## <a name="see-also"></a>関連項目

- [引数の値渡しと参照渡し](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [拡大変換と縮小変換](../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
