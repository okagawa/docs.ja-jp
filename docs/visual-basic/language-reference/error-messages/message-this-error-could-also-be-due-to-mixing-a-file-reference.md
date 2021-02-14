---
description: "詳細情報: BC30971:<message> このエラーは、ファイル参照とアセンブリ '<assemblyname>' へのプロジェクト参照との混合によって生じた可能性があります"
title: <message> このエラーは、ファイル参照と '<assemblyname>' へのプロジェクト参照との混合によって生じた可能性があります。
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: c3b7c27c3f253389cd0a8e725ddcae3816c612b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795847"
---
# <a name="bc30971-message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a>BC30971:\<message> このエラーは、ファイル参照と '\<assemblyname>' へのプロジェクト参照との混合によって生じた可能性があります。

\<message> このエラーは、ファイル参照とアセンブリ '\<assemblyname> へのプロジェクト参照との混合によって生じた可能性があります。 この場合、プロジェクト '\<projectname1>' の '\<assemblyfilename>' へのファイル参照を '\<projectname2>' へのプロジェクト参照で置き換えてください。

 プロジェクト内のコードが別のプロジェクトのメンバーにアクセスしていますが、ソリューションが Visual Basic コンパイラに参照の解決を許可するよう構成されていません。

 別のアセンブリで定義されている型にアクセスするには、そのアセンブリへの参照を Visual Basic コンパイラが保持する必要があります。 これは、プロジェクト間の循環参照にならない、単一であいまいさのない参照である必要があります。

 **エラー ID:** BC30971

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. どのプロジェクトが、プロジェクトからの参照に最適なアセンブリを作成しているか特定します。 この判断には、ファイル アクセスの容易さや更新の頻度などの基準を使用できます。

2. プロジェクトのプロパティに、使用する型が定義されているアセンブリを含むプロジェクトへの参照を追加します。

## <a name="see-also"></a>関連項目

- [プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)
- [宣言された要素の参照](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
- [壊れた参照のトラブルシューティング](/visualstudio/ide/troubleshooting-broken-references)
