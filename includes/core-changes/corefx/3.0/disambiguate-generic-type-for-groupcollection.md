---
ms.openlocfilehash: 97fab784acac4331894547eea27fc21b485597fb
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366885"
---
### <a name="passing-groupcollection-to-extension-methods-taking-ienumerablet-requires-disambiguation"></a>IEnumerable\<T> を受け取る拡張メソッドに GroupCollection を渡すにはあいまいさが必要

<xref:System.Text.RegularExpressions.GroupCollection> で `IEnumerable<T>` を受け取る拡張メソッドを呼び出す場合は、キャストを使用して型を明確にする必要があります。

#### <a name="change-description"></a>変更内容

.NET Core 3.0 以降では、<xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> によって `IEnumerable<KeyValuePair<String,Group>>` が実装され、それによって他の型 (`IEnumerable<Group>` など) も加えて実装されます。 これは、<xref:System.Collections.Generic.IEnumerable%601> を受け取る拡張メソッドを呼び出す場合には、あいまいな結果となります。 たとえば、<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType> などの <xref:System.Text.RegularExpressions.GroupCollection> インスタンスでこのような拡張メソッドを呼び出すと、次のコンパイラ エラーが表示されます。

**CS1061: 'GroupCollection' に 'Count' の定義が含まれておらず、型 'GroupCollection' の最初の引数を受け付ける拡張メソッド 'Count' が見つかりませんでした (using ディレクティブまたはアセンブリ参照が不足しています。)**

以前のバージョンの .NET では、あいまいさはなく、コンパイラ エラーもありませんでした。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="reason-for-change"></a>変更理由

これは[意図しない破壊的変更](https://github.com/dotnet/corefx/pull/30077)でした。 しばらくの間このようになっているため、元に戻す予定はありません。 また、このような変更自体が中断されます。

#### <a name="recommended-action"></a>推奨アクション

<xref:System.Text.RegularExpressions.GroupCollection> インスタンスの場合は、キャストで `IEnumerable<T>` を受け入れる拡張メソッドの呼び出しを明確にします。

```csharp
// Without a cast - causes CS1061.
match.Groups.Count(_ => true)

// With a disambiguating cast.
((IEnumerable<Group>)m.Groups).Count(_ => true);
```

#### <a name="category"></a>カテゴリ

Core .NET ライブラリ

#### <a name="affected-apis"></a>影響を受ける API

<xref:System.Collections.Generic.IEnumerable%601> を受け入れるすべての拡張メソッドが影響を受けます。 次に例を示します。

- <xref:System.Collections.Immutable.ImmutableArray.ToImmutableArray%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableDictionary.ToImmutableDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableHashSet.ToImmutableHashSet%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableList.ToImmutableList%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedDictionary.ToImmutableSortedDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedSet.ToImmutableSortedSet%2A?displayProperty=fullName>
- <xref:System.Data.DataTableExtensions.CopyToDataTable%2A?displayProperty=fullName>
- `System.Linq.Enumerable` メソッドの大部分 (<xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName> など)
- <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName>

<!--

#### Affected APIs

- ``M:System.Collections.Immutable.ImmutableArray.ToImmutableArray``1(System.Collections.Generic.IEnumerable{``0})``
- `Overload:System.Collections.Immutable.ImmutableDictionary.ToImmutableDictionary`
- `Overload:System.Collections.Immutable.ImmutableHashSet.ToImmutableHashSet`
- ``M:System.Collections.Immutable.ImmutableList.ToImmutableList``1(System.Collections.Generic.IEnumerable{``0})``
- `Overload:System.Collections.Immutable.ImmutableSortedDictionary.ToImmutableSortedDictionary`
- `Overload:System.Collections.Immutable.ImmutableSortedSet.ToImmutableSortedSet`
- `Overload:System.Data.DataTableExtensions.CopyToDataTable`
- `Overload:System.Linq.Enumerable.Count`
- `Overload:System.Linq.ParallelEnumerable.AsParallel`
- `Overload:System.Linq.Queryable.AsQueryable`

-->
