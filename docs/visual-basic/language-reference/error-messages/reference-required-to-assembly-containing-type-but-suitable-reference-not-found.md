---
description: "詳細情報: BC30969:参照には型 '<assemblyidentity>' を含むアセンブリ '<typename>' が必要ですが、プロジェクト '<projectname1>' と '<projectname2>' があいまいであるため、適切な参照が見つかりませんでした。"
title: 参照には型 '<assemblyidentity>' を含むアセンブリ '<typename>' が必要ですが、プロジェクト '<projectname1>' と '<projectname2>' があいまいであるため、適切な参照が見つかりませんでした。
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 93713fe2175c303b7d126a7c3d5e33f9990955a1
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481663"
---
# <a name="bc30969-reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a>BC30969:参照には型 '\<assemblyidentity>' を含むアセンブリ '\<typename>' が必要ですが、プロジェクト '\<projectname1>' と '\<projectname2>' があいまいであるため、適切な参照が見つかりませんでした。

プロジェクト外で定義されているクラス、構造体、インターフェイス、列挙型、デリゲートなどの型が式で使用されています。 しかし、その型を定義する複数のアセンブリへのプロジェクト参照があります。

 問題のプロジェクトは、同じ名前のアセンブリを複数作成します。 このため、コンパイラは、アクセスしている型にどちらのアセンブリを使用すればよいかを判断できません。

 別のアセンブリで定義されている型にアクセスするには、そのアセンブリへの参照を Visual Basic コンパイラが保持する必要があります。 これは、プロジェクト間の循環参照にならない、単一であいまいさのない参照である必要があります。

 **エラー ID:** BC30969

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. どのプロジェクトが、プロジェクトからの参照に最適なアセンブリを作成しているか特定します。 この判断には、ファイル アクセスの容易さや更新の頻度などの基準を使用できます。

2. プロジェクトのプロパティに、使用する型が定義されているアセンブリを含むファイルへの参照を追加します。

## <a name="see-also"></a>関連項目

- [プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)
- [宣言された要素の参照](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
- [壊れた参照のトラブルシューティング](/visualstudio/ide/troubleshooting-broken-references)
