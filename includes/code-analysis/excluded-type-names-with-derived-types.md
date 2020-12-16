---
ms.openlocfilehash: 4125df1d64fe7f3f2eb1eb4a821ed46c8270c95f
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97531921"
---
### <a name="exclude-specific-types-and-their-derived-types"></a>特定の型とその派生型を除外する

分析から特定の型とその派生型を除外できます。 たとえば、という名前の型とその派生型内のメソッドで規則を実行しないように指定するには、 `MyType` 次のキーと値のペアをプロジェクトの *editorconfig* ファイルに追加します。

```ini
dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType
```

オプションの値で使用できるシンボル名の形式 (で区切られてい `|` ます):

- 型名のみ (包含する型または名前空間に関係なく、名前を持つすべての型が含まれます)。
- シンボルの [ドキュメント ID 形式](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)で、省略可能なプレフィックスを持つ完全修飾名 `T:` 。

例:

| オプション値 | まとめ |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType` | `MyType`と、そのすべての派生型と一致するすべての型を照合します。 |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType1|MyType2` | `MyType1`または `MyType2` すべての派生型のいずれかという名前のすべての型と一致します。 |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS.MyType` | `MyType`指定された完全修飾名とそのすべての派生型を使用して、特定の型を照合します。 |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS1.MyType1|M:NS2.MyType2` | 特定の型 `MyType1` と、 `MyType2` それぞれの完全修飾名、およびそのすべての派生型を照合します。 |
