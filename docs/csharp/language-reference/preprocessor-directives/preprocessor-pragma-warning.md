---
description: '#pragma warning - C# リファレンス'
title: '#pragma warning - C# リファレンス'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 16582a74bd34f2c0d89950280f1d5fde25435eea
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215993"
---
# <a name="pragma-warning-c-reference"></a>#pragma 警告 (C# リファレンス)

`#pragma warning` を使用すると、特定の警告を有効または無効にすることができます。

## <a name="syntax"></a>構文

```csharp
#pragma warning disable warning-list
#pragma warning restore warning-list
```

## <a name="parameters"></a>パラメーター

 `warning-list` 警告番号のコンマ区切りのリスト。 "CS" というプレフィックスは省略可能です。

 警告番号が指定されていないと、`disable` はすべての警告を無効にし、`restore` はすべての警告を有効にします。

> [!NOTE]
> Visual Studio で警告番号を調べるには、プロジェクトをビルドし、**[出力]** ウィンドウで警告番号を探してください。

## <a name="example"></a>例

```csharp
// pragma_warning.cs
using System;

#pragma warning disable 414, CS3021
[CLSCompliant(false)]
public class C
{
    int i = 1;
    static void Main()
    {
    }
}
#pragma warning restore CS3021
[CLSCompliant(false)]  // CS3021
public class D
{
    int i = 1;
    public static void F()
    {
    }
}
```

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# プリプロセッサ ディレクティブ](./index.md)
- [C# コンパイラ エラー](../compiler-messages/index.md)
- [コード分析の警告を抑制する方法](../../../fundamentals/code-analysis/suppress-warnings.md)
