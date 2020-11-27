---
description: '#Null 許容 - C# リファレンス'
title: '#Null 許容 - C# リファレンス'
ms.date: 11/18/2020
f1_keywords:
- '#nullable'
helpviewer_keywords:
- '#nullable directive [C#]'
ms.openlocfilehash: 4c114a09f29769fcc824bcdabdc1d523e33f199d
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099447"
---
# <a name="nullable-c-reference"></a>#nullable - C# リファレンス

`#nullable` プリプロセッサ ディレクティブは、"*Null 許容注釈コンテキスト*" と "*Null 許容警告コンテキスト*" を設定します。 このディレクティブでは、Null 許容注釈の効果があるかどうか、および NULL 値の許容の警告が与えられるかどうかが制御されます。 各コンテキストは "*無効*" または "*有効*" になります。

どちらのコンテキストもプロジェクト レベル (C# ソース コードの外部) で指定することができます。 `#nullable` ディレクティブは、注釈と警告のコンテキストを制御し、プロジェクト レベルの設定よりも優先されます。 ディレクティブは、別のディレクティブがそれをオーバーライドするか、ソース ファイルの末尾に達するまで、制御するコンテキストを設定します。

ディレクティブの効果は次のとおりです。

- `#nullable disable`: Null 許容注釈および警告コンテキストを "*無効*" に設定します。
- `#nullable enable`: Null 許容注釈および警告コンテキストを "*有効*" に設定します。
- `#nullable restore`: Null 許容注釈および警告コンテキストを、プロジェクト設定に復元します。
- `#nullable disable annotations`: Null 許容注釈コンテキストを "*無効*" に設定します。
- `#nullable enable annotations`: Null 許容注釈コンテキストを "*有効*" に設定します。
- `#nullable restore annotations`: Null 許容注釈コンテキストを、プロジェクト設定に復元します。
- `#nullable disable warnings`: Null 許容警告コンテキストを "*無効*" に設定します。
- `#nullable enable warnings`: Null 許容警告コンテキストを "*有効*" に設定します。
- `#nullable restore warnings`: Null 許容警告コンテキストをプロジェクト設定に復元します。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# プリプロセッサ ディレクティブ](./index.md)
