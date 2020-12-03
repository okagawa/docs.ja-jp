---
title: '破壊的変更:CA2015: MemoryManager<T> から派生した型にはファイナライザーを定義しません'
description: コード分析ルール CA2015 の有効化によって発生する .NET 5.0 での破壊的変更について学習します。
ms.date: 09/03/2020
ms.openlocfilehash: 5d0ba0546b5a72363559f23713c8af4bb4e26e48
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759318"
---
# <a name="warning-ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert"></a>警告 CA2015:MemoryManager\<T> から派生した型にはファイナライザーを定義しません

.NET コード アナライザー ルール [CA2015](/visualstudio/code-quality/ca2015) は、.NET 5.0 以降では既定で有効になっています。 ファイナライザーを定義する <xref:System.Buffers.MemoryManager%601> から派生したすべての型に対して、ビルドの警告が生成されます。

## <a name="change-description"></a>変更内容

.NET 5.0 以降、.NET SDK には [.NET ソース コード アナライザー](../../../../fundamentals/code-analysis/overview.md)が含まれています。 これらのルールのいくつかは、[CA2015](/visualstudio/code-quality/ca2015) を含め、既定で有効になっています。 このルールに違反し、警告をエラーとして扱うように構成されているコードがプロジェクトに含まれている場合、この変更によってビルドが破損する可能性があります。

ルール CA2015 によって、ファイナライザーを定義する <xref:System.Buffers.MemoryManager%601> から派生した型にフラグが設定されます。 <xref:System.Buffers.MemoryManager%601> から派生した型にファイナライザーを追加すると、バグが示される可能性があります。 <xref:System.Span%601> で取得されたネイティブ リソースはクリーンアップされている可能性がありますが、<xref:System.Span%601> によって引き続き使用されている可能性もあります。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

- ファイナライザーの定義を削除します。 詳細については、[CA2015](/visualstudio/code-quality/ca2015) に関する記事を参照してください。

- コード分析を完全に無効にするには、プロジェクト ファイルで `EnableNETAnalyzers` を `false` に設定します。 詳細については、「[EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)」を参照してください。

## <a name="affected-apis"></a>影響を受ける API

API 分析では検出できません。

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
