---
description: "詳細情報: BC36550:'Extension' 属性は 'Module'、'Sub'、または 'Function' の各宣言にのみ適用できます"
title: "'Extension' 属性は 'Module'、'Sub'、または 'Function' の各宣言にのみ適用できます"
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: f0c87de34238974229bc572a0f634a16e8cc78d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796315"
---
# <a name="bc36550-extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>BC36550:'Extension' 属性は 'Module'、'Sub'、または 'Function' の各宣言にのみ適用できます

Visual Basic でデータ型を拡張する唯一の方法は、標準モジュール内で拡張メソッドを定義することです。 拡張メソッドになるのは、`Sub` プロシージャまたは `Function` プロシージャです。 すべての拡張メソッドは、<xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 名前空間の拡張属性 `<Extension()>` でマークする必要があります。 必要に応じて、拡張メソッドを含むモジュールを同じ方法でマークすることもできます。 その他の拡張属性の使用は有効ではありません。

**エラー ID:** BC36550

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 拡張属性を削除します。

- それを囲むモジュールに定義されているメソッドとして拡張機能を再設計します。

## <a name="example"></a>例

`String` データ型の `Print` メソッドを定義する例を次に示します。

```vb
Imports StringUtility
Imports System.Runtime.CompilerServices
Namespace StringUtility
    <Extension()>
    Module StringExtensions
        <Extension()>
        Public Sub Print (ByVal str As String)
            Console.WriteLine(str)
        End Sub
    End Module
End Namespace
```

## <a name="see-also"></a>関連項目

- [属性の概要](../../programming-guide/concepts/attributes/index.md)
- [拡張メソッド](../../programming-guide/language-features/procedures/extension-methods.md)
- [Module ステートメント](../statements/module-statement.md)
