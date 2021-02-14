---
description: '詳細情報: コレクションに関するガイドライン'
title: コレクションに関するガイドライン
ms.date: 10/22/2008
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
ms.openlocfilehash: fa189068e9f3e06b3e88999bd4b0ea0998cd16e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642033"
---
# <a name="guidelines-for-collections"></a>コレクションに関するガイドライン

共通の特性をいくつか持つオブジェクトのグループを操作するために特に設計された型はすべて、コレクションと見なすことができます。 ほとんどの場合、そのような型には <xref:System.Collections.IEnumerable> または <xref:System.Collections.Generic.IEnumerable%601> を実装するのが適しているので、このセクションでは、それらのインターフェイスのいずれかまたは両方を実装している型のみを、コレクションとして考えます。

 ❌ パブリック API では、弱く型指定されたコレクションを使用しないでください。

 コレクション項目を表すすべての戻り値とパラメーターの型は、その基本データ型のいずれか (これは、コレクションのパブリック メンバーにのみ適用されます) ではなく、項目の完全な型にする必要があります。

 ❌ パブリック API では、<xref:System.Collections.ArrayList> または <xref:System.Collections.Generic.List%601> を使用しないでください。

 これらの型は、パブリック API ではなく、内部実装で使用するように設計されたデータ構造です。 `List<T>` は、API のクリーンさと柔軟性を犠牲にする代わりに、パフォーマンスとパワーに最適化されています。 たとえば、`List<T>` を返した場合、クライアント コードによってコレクションが変更されても通知を受け取ることはできません。 また、`List<T>` によって <xref:System.Collections.Generic.List%601.BinarySearch%2A> などの多くのメンバーが公開されていますが、それらは多くのシナリオでは役に立たないか、適用できません。 次の 2 つのセクションでは、パブリック API 専用に設計されている型 (抽象化) について説明します。

 ❌ パブリック API では、`Hashtable` または `Dictionary<TKey,TValue>` を使用しないでください。

 これらの型は、内部実装で使用するように設計されたデータ構造です。 パブリック API では、<xref:System.Collections.IDictionary>、`IDictionary <TKey, TValue>`、またはこれらのインターフェイスの一方か両方が実装されているカスタム型を使用する必要があります。

 ❌ `GetEnumerator` メソッドの戻り値の型として使用する場合を除き、<xref:System.Collections.Generic.IEnumerator%601>、<xref:System.Collections.IEnumerator>、またはこれらのインターフェイスのいずれかが実装されている他の型を使用しないでください。

 `GetEnumerator` 以外のメソッドから列挙子を返す型を、`foreach` ステートメントと共に使用することはできません。

 ❌ `IEnumerator<T>` と `IEnumerable<T>` の両方を同じ型で実装しないでください。 同じことが、非ジェネリック インターフェイスの `IEnumerator` と `IEnumerable` にも当てはまります。

## <a name="collection-parameters"></a>コレクションのパラメーター

 ✔️ パラメーターの型としては、可能な限り最も特殊化されていない型を使用してください。 パラメーターとしてコレクションを受け取るほとんどのメンバーは、`IEnumerable<T>` インターフェイスを使用します。

 ❌ `Count` プロパティにアクセスするためだけに、パラメーターとして <xref:System.Collections.Generic.ICollection%601> または <xref:System.Collections.ICollection> を使用しないでください。

 代わりに、`IEnumerable<T>` または `IEnumerable` を使用し、オブジェクトで `ICollection<T>` または `ICollection` が実装されているかどうかを動的にチェックすることを検討します。

## <a name="collection-properties-and-return-values"></a>コレクションのプロパティと戻り値

 ❌ 設定可能なコレクション プロパティを提供しないでください。

 ユーザーは、最初にコレクションをクリアしてから、新しい内容を追加することで、コレクションの内容を置き換えることができます。 コレクション全体を置き換えるのが一般的なシナリオである場合は、コレクションで `AddRange` メソッドを提供することを検討します。

 ✔️ 読み取り/書き込みコレクションを表すプロパティまたは戻り値の場合は、`Collection<T>` または `Collection<T>` のサブクラスを使用します。

 `Collection<T>` によって満たされない要件がある場合は (たとえば、コレクションで <xref:System.Collections.IList> が実装されていてはならない)、`IEnumerable<T>`、`ICollection<T>`、または <xref:System.Collections.Generic.IList%601> を実装してカスタム コレクションを使用します。

 ✔️ 読み取り専用コレクションを表すプロパティまたは戻り値の場合は、<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>、`ReadOnlyCollection<T>` のサブクラス、またはまれに `IEnumerable<T>` を使用します。

 一般には、`ReadOnlyCollection<T>` が推奨されます。 満たされない要件がある場合は (たとえば、コレクションで `IList` が実装されていてはならない)、`IEnumerable<T>`、`ICollection<T>`、または `IList<T>` を実装してカスタム コレクションを使用します。 読み取り専用のカスタム コレクションを実装する場合は、`ICollection<T>.IsReadOnly` を実装して `true` を返します。

 サポートする必要があるシナリオが、順方向のみの反復だけであることが確実な場合は、単に `IEnumerable<T>` を使用できます。

 ✔️ コレクションを直接使用するのではなく、ジェネリック基本コレクションのサブクラスの使用を検討します。

 このようにすると、より適切な名前を使用したり、基本コレクション型に存在しないヘルパー メンバーを追加したりすることができます。 これは、高レベルの API に特に当てはまります。

 ✔️ 非常によく使用されるメソッドとプロパティからは、`Collection<T>` または `ReadOnlyCollection<T>` のサブクラスを返すことを検討します。

 これにより、後でヘルパー メソッドを追加したり、コレクションの実装を変更したりできるようになります。

 ✔️ コレクションに格納される項目に一意のキー (名前、ID など) がある場合は、キー付きコレクションを使用することを検討します。 キー付きコレクションは、整数とキーの両方でインデックスを作成できるコレクションであり、通常は `KeyedCollection<TKey,TItem>` を継承することによって実装されます。

 通常、キー付きコレクションはメモリ占有領域が大きいため、メモリのオーバーヘッドがキーを使用する利点を上回る場合は使用しないでください。

 ❌ コレクションのプロパティから、またはコレクションを返すメソッドからは、null 値を返さないでください。 代わりに空のコレクションまたは空の配列を返します。

 一般的なルールとして、null と空の (0 項目) のコレクションまたは配列は、同じように扱う必要があります。

### <a name="snapshots-versus-live-collections"></a>スナップショットとライブ コレクション

 ある時点での状態を表すコレクションは、スナップショット コレクションと呼ばれます。 たとえば、データベース クエリから返された行が格納されるコレクションはスナップショットです。 常に現在の状態を表すコレクションは、ライブ コレクションと呼ばれます。 たとえば、`ComboBox` 項目のコレクションはライブ コレクションです。

 ❌ プロパティからスナップショット コレクションを返さないでください。 プロパティからはライブ コレクションを返す必要があります。

 プロパティのゲッターは、非常に軽量な操作にする必要があります。 スナップショットを返すには、O(n) 操作で内部コレクションのコピーを作成する必要があります。

 ✔️ 揮発性である (つまり、コレクションを明示的に変更しなくても、変化する可能性がある) コレクションを表すには、スナップショット コレクションまたはライブ `IEnumerable<T>` (またはそのサブタイプ) のいずれかを使用します。

 一般に、共有リソース (ディレクトリ内のファイルなど) を表すコレクションはすべて揮発性です。 そのようなコレクションは、実装が単に順方向のみの列挙子である場合を除き、ライブ コレクションとして実装するのは非常に困難または不可能です。

## <a name="choosing-between-arrays-and-collections"></a>配列とコレクションの選択

 ✔️ 配列よりコレクションを優先します。

 コレクションの方が、内容をきめ細かく制御でき、時間と共に発展でき、いっそう便利です。 さらに、配列の複製にかかるコストは膨大であるため、読み取り専用のシナリオに配列を使用することはお勧めしません。 使いやすさの研究では、一部の開発者はコレクション ベースの API を使用する方が快適であることが示されています。

 ただし、低レベルの API を開発している場合は、読み取り/書き込みのシナリオには配列を使用する方が適切な場合があります。 配列の方がメモリ占有領域が小さいため、作業セットを減らすことができます。また、配列内の要素へのアクセスは、ランタイムによって最適化されるため、より高速になります。

 ✔️ メモリ消費を最小限に抑え、パフォーマンスを最大にするため、低レベルの API では配列を使用することを検討します。

 ✔️ バイトのコレクションではなく、バイト配列を使用します。

 ❌ プロパティ ゲッターが呼び出されるたびに、プロパティから新しい配列 (内部配列のコピーなど) を返す必要がある場合は、プロパティに配列を使用しないでください。

## <a name="implementing-custom-collections"></a>カスタム コレクションの実装

 ✔️ 新しいコレクションを設計するときは、`Collection<T>`、`ReadOnlyCollection<T>`、または `KeyedCollection<TKey,TItem>` から継承することを検討します。

 ✔️ 新しいコレクションを設計するときは、`IEnumerable<T>` を実装します。 合理的である場合は、`ICollection<T>` または `IList<T>` を実装することを検討します。

 そのようなカスタム コレクションを実装するときは、`Collection<T>` および `ReadOnlyCollection<T>` によって確立されている API パターンに、可能な限り忠実に従います。 つまり、同じメンバーを明示的に実装する、これら 2 つのコレクションと同じようにパラメーターに名前を付ける、といったことです。

 ✔️ これらのインターフェイスを入力として受け取る API にコレクションを頻繁に渡す場合は、非ジェネリック コレクション インターフェイス (`IList` と `ICollection`) を実装することを検討します。

 ❌ コレクションの概念と関係のない複雑な API のある型に、コレクション インターフェイスを実装しないでください。

 ❌ `CollectionBase` などの非ジェネリック基本コレクションから継承しないでください。 代わりに `Collection<T>`、`ReadOnlyCollection<T>`、および `KeyedCollection<TKey,TItem>` 型を使用してください。

### <a name="naming-custom-collections"></a>カスタム コレクションの名前付け

 コレクション (`IEnumerable` を実装する型) は、主に次の 2 つの理由で作成されます。(1) 構造固有の操作があり、多くの場合は既存のデータ構造 (<xref:System.Collections.Generic.List%601>、<xref:System.Collections.Generic.LinkedList%601>、<xref:System.Collections.Generic.Stack%601> など) と異なるパフォーマンス特性を持つ、新しいデータ構造を作成する、(2) 特定の項目のセットを保持するための特殊なコレクションを作成する (例: <xref:System.Collections.Specialized.StringCollection>)。 データ構造は、アプリケーションやライブラリの内部実装で最もよく使用されます。 特殊なコレクションは、主に API で公開されます (プロパティとパラメーターの型として)。

 ✔️ `IDictionary` または `IDictionary<TKey,TValue>` を実装する抽象化の名前では、"Dictionary" サフィックスを使用します。

 ✔️ `IEnumerable` (またはその子孫) を実装し、項目のリストを表す型の名前では、"Collection" サフィックスを使用します。

 ✔️ カスタム データ構造には、適切なデータ構造名を使用します。

 ❌ コレクションの抽象化の名前では、"LinkedList" や "Hashtable" など、特定の実装を意味するサフィックスを使用しないでください。

 ✔️ コレクションの名前には、項目の型の名前をプレフィックスとして付けることを検討します。 たとえば、(`IEnumerable<Address>` を実装する) `Address` 型の項目を格納するコレクションの名前は、`AddressCollection` にする必要があります。 項目の型がインターフェイスの場合は、項目の型の "I" プレフィックスを省略できます。 したがって、<xref:System.IDisposable> 項目のコレクションは、`DisposableCollection` という名前にできます。

 ✔️ フレームワークに対応する書き込み可能なコレクションが追加される可能性がある場合、または既に存在する場合は、読み取り専用コレクションの名前に "ReadOnly" プレフィックスを使用することを検討します。

 たとえば、文字列の読み取り専用コレクションの名前は、`ReadOnlyStringCollection` にする必要があります。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
- [使用方法のガイドライン](usage-guidelines.md)
