---
title: ドキュメントルール (コード分析)
description: コード分析ルールのドキュメントルールの詳細
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- warnings, documentation
author: mavasani
ms.author: mavasani
ms.openlocfilehash: 29d1734eec29bd00d456b4b00c48c2e8ef223441
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2020
ms.locfileid: "96591280"
---
# <a name="documentation-rules"></a>ドキュメント規則

ドキュメントルールでは、外部から参照可能な Api に [XML ドキュメントコメント](../../../csharp/codedoc.md) を適切に使用することで、適切にドキュメント化されたライブラリの作成をサポートしています。

## <a name="in-this-section"></a>このセクションの内容

| ルール | 説明 |
| - | - |
| [CA1200:プレフィックスで cref タグを使用しません](ca1200.md) | XML ドキュメントタグの [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) 属性は、"コード参照" を意味します。 タグの内部テキストが、型、メソッド、プロパティなど、コード要素であることを指定します。 プレフィックスでタグを使用するのは避けて `cref` ください。これにより、コンパイラが参照を検証できなくなります。 また、Visual Studio 統合開発環境 (IDE: integrated development environment) が、リファクタリング中にこれらのシンボル参照を検索および更新できないようにします。 |
