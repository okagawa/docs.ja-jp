---
description: 詳細については、「' Object ' 型の引数を使用するときに ' FileGet ' ではなく ' FileGetObject ' を使用する」を参照してください。
title: 型 'Object' の引数を使用する場合は、'FileGet' ではなく 'FileGetObject' を使用してください。
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 4481fdced961cacf0e652c141601efa13bec776b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471163"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a>型 'Object' の引数を使用する場合は、'FileGet' ではなく 'FileGetObject' を使用してください。

`FileGet` メソッドには、型 `Object`の引数が含まれています。 あいまいさを避けるため、`FileGetObject` の代わりに `FileGet` を使用する必要があります。  
  
 `My.Computer.Filesystem` によって提供される機能は、`FileGet` または `FileGetObject` よりも使いやすく、パフォーマンスが優れています。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. `FileGet` を `FileGetObject` で置き換え  
  
2. `Object` 引数をより具体的な種類にキャストします。  
  
## <a name="see-also"></a>関連項目

- [マイファイル (コンピューター)](xref:Microsoft.VisualBasic.FileIO.FileSystem)
