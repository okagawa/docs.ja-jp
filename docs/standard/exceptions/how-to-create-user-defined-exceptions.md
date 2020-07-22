---
title: '方法: ユーザー定義の例外を作成する'
description: .NET で例外基底クラスから派生した例外クラスの階層の代わりとして、ユーザー定義の例外を作成する方法について説明します。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
ms.openlocfilehash: 14eb6246ba4347f33766f7dff36463f2bf996330
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662798"
---
# <a name="how-to-create-user-defined-exceptions"></a>ユーザー定義の例外を作成する方法

.NET では、基底クラス <xref:System.Exception> から最終的に派生した例外クラスの階層構造を提供します。 ただし、定義済みの例外のいずれも要件を満たさない場合は、<xref:System.Exception> クラスから派生することによって、独自の例外クラスを作成できます。

独自の例外を作成するときに、ユーザー定義の例外のクラス名の末尾に "Exception" という単語を付加し、次の例で示すように、3 つの共通コンストラクターを実装します。 例では、`EmployeeListNotFoundException` という名前の新しい例外クラスを定義します。 このクラスは <xref:System.Exception> から派生し、次の 3 つのコンストラクターが含まれています。

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> リモート処理を使用している場合は、任意のユーザー定義の例外のメタデータがサーバー側 (呼び出し先) とクライアント (プロキシ オブジェクトまたは呼び出し元) で使用できることを保証する必要があります。 詳細については、「[例外の推奨事項](best-practices-for-exceptions.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [例外](index.md)
