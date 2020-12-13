---
ms.openlocfilehash: 83644b9205d650da68c910095dd1d22a14940c44
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97366857"
---
### <a name="exclude-specific-symbols"></a>特定のシンボルを除外する

型やメソッドなど、特定のシンボルを分析から除外することができます。 たとえば、という名前の型内のどのコードでもルールを実行しないように指定するには、 `MyType` プロジェクトの *editorconfig* ファイルに次のキーと値のペアを追加します。

```ini
dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType
```

オプションの値で使用できるシンボル名の形式 (で区切られてい `|` ます):

- シンボル名のみ (包含する型または名前空間に関係なく、名前の付いたすべての記号が含まれます)。
- シンボルの [ドキュメント ID 形式](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)の完全修飾名。 各シンボル名には、 `M:` メソッドの場合、型の場合は、 `T:` 名前空間の場合など、シンボルの種類のプレフィックスが必要です `N:` 。
- `.ctor` コンストラクターの場合は、 `.cctor` 静的コンストラクターの場合は。

例 :

| オプション値 | まとめ |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType` | という名前 `MyType` のすべての記号を検索します。 |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType1|MyType2` | またはという名前のすべての記号と一致 `MyType1` `MyType2` します。 |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS.MyType.MyMethod(ParamType)` | `MyMethod`指定した完全修飾シグネチャと特定のメソッドを照合します。 |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS1.MyType1.MyMethod1(ParamType)|M:NS2.MyType2.MyMethod2(ParamType)` | 特定のメソッド `MyMethod1` と、 `MyMethod2` それぞれの完全修飾署名を照合します。 |
