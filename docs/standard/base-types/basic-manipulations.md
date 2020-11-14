---
title: .NET の基本的な文字列操作
description: 多くの文字列メソッドを呼び出す例を確認します。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: 659f01cc1d7ae03e12e83329e4fd2446b7512475
ms.sourcegitcommit: ffd4d5e824db6c5f0c3521c0e802fd9e8f0edcbe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93342619"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>方法: .NET の基本的な文字列操作を実行する

次の例では、「[基本的な文字列操作](basic-string-operations.md)」のトピックで説明したいくつかの方法を使用して、実際のアプリケーションで見られる方法で文字列の操作を実行するクラスを構築します。 `MailToData` クラスは、個人の名前とアドレスを個別のプロパティに格納し、`City`、`State`、`Zip` フィールドを組み合わせて、ユーザーに表示する1 つの文字列にする方法を提供します。 さらに、そのクラスを使用すると、ユーザーは市区町村、都道府県、郵便番号の情報を 1 つの文字列として入力できます。 アプリケーションにより、1 つの文字列が自動的に解析され、対応するプロパティに適切な情報が入力されます。

わかりやすいように、この例ではコマンド ライン インターフェイスによるコンソール アプリケーションを使用します。

## <a name="example"></a>例

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]

上記のコードを実行すると、ユーザーは自分の名前とアドレスを入力するように求められます。 アプリケーションにより、適切なプロパティに情報が格納され、市区町村、都道府県、郵便番号の情報を表示する 1 つの文字列が作成されて、ユーザーに情報が表示されます。

## <a name="see-also"></a>関連項目

- [基本的な文字列操作](basic-string-operations.md)
