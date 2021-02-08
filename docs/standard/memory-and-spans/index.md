---
description: '詳細情報: メモリおよびスパンに関連する型'
title: メモリとスパン
ms.date: 10/03/2018
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
ms.openlocfilehash: c151632db0fdfff388f1aba95fd9b0edc940ae0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731696"
---
# <a name="memory--and-span-related-types"></a>メモリおよびスパンに関連する型

.NET Core 2.1 以降、.NET には、任意のメモリの厳密に型指定された連続する領域を表す、相互に関連する型が多数含まれています。 次の設定があります。

- <xref:System.Span%601?displayProperty=nameWithType>: メモリの連続した領域にアクセスするために使う型です。 <xref:System.Span%601> インスタンスは、`T` 型の配列、<xref:System.String>、[stackalloc](../../csharp/language-reference/operators/stackalloc.md) を使って割り当てたバッファー、またはアンマネージ メモリへのポインターによってバックアップできます。 これはスタック上に割り当てる必要があるため、いくつかの制限があります。 たとえば、クラス内のフィールドを <xref:System.Span%601> 型にすることはできませんし、非同期操作でスパンを使うこともできません。

- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>: <xref:System.Span%601> 構造体の変更できないバージョンです。

- <xref:System.Memory%601?displayProperty=nameWithType>: メモリの隣接した領域に対するラッパーです。 <xref:System.Memory%601> インスタンスは、`T` 型の配列、<xref:System.String>、またはメモリ マネージャーによってバックアップできます。 これはマネージド ヒープに格納できるため、<xref:System.Memory%601> には <xref:System.Span%601> の制限事項はありません。

- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>: <xref:System.Memory%601> 構造体の変更できないバージョンです。

- <xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>: メモリ プールの厳密に型指定されたメモリ ブロックを、所有者に割り当てます。 <xref:System.Buffers.IMemoryOwner%601> インスタンスは、<xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> を呼び出すことでプールから借りてくることができ、<xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType> を呼び出すことでプールにリリースします。

- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>: メモリ ブロックの所有者を表し、その有効期間の管理をコントロールします。

- <xref:System.Buffers.MemoryManager%601>: <xref:System.Memory%601> をセーフ ハンドルなどのその他の型でバックアップできるようにするために、<xref:System.Memory%601> の実装を置き換えるために使用できる抽象基本クラスです。 <xref:System.Buffers.MemoryManager%601> は高度なシナリオ向けです。

- <xref:System.ArraySegment%601>: 特定のインデックスから始まる、特定の数の配列要素のラッパーです。

- <xref:System.MemoryExtensions?displayProperty=nameWithType>: 文字列、配列、および配列セグメントを、<xref:System.Memory%601> ブロックに変換するための拡張メソッドのコレクションです。

<xref:System.Span%601?displayProperty=nameWithType>、<xref:System.Memory%601?displayProperty=nameWithType>、およびそれらに対応する読み取り専用の型は、必要以上にメモリをコピーしたり、マネージド ヒープに割り当てたりすることのないアルゴリズムを作成できるように設計されています。 (`Slice` またはそれらのコンストラクターを使用して) それらを作成しても、基になるバッファーの複製は行われません。ラップされたメモリの "ビュー" を表す関連する参照とオフセットのみが更新されます。

> [!NOTE]
> 以前のフレームワークでは、[System.Memory NuGet パッケージ](https://www.nuget.org/packages/System.Memory/)で <xref:System.Span%601> と <xref:System.Memory%601> を利用できます。

詳細については、「<xref:System.Buffers?displayProperty=nameWithType>」を参照してください。

## <a name="working-with-memory-and-span"></a>メモリとスパンを使った作業

通常、メモリおよびスパンに関連する型は処理パイプラインにデータを格納するために使われます。そのため開発者は、<xref:System.Span%601>、<xref:System.Memory%601>、および関連する型を使う場合に、一連のベスト プラクティスに従うことが重要です。 これらのベスト プラクティスは、「[Memory\<T>T> と Span\<T>T> の使用ガイドライン](memory-t-usage-guidelines.md)」でドキュメント化されています。

## <a name="see-also"></a>関連項目

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
