---
description: "詳細情報: BC30251:型 '<typename>' にはコンストラクターがありません。"
title: 型 '<typename>' にはコンストラクターがありません。
ms.date: 07/20/2015
f1_keywords:
- bc30251
- vbc30251
helpviewer_keywords:
- BC30251
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
ms.openlocfilehash: 32ae854e9f1b037a17d9c378ce7ee4a3f9b43ad2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641175"
---
# <a name="bc30251-type-typename-has-no-constructors"></a>BC30251:型 '\<typename>' にはコンストラクターがありません。

型が `Sub New()` の呼び出しをサポートしません。 コンパイラまたはバイナリ ファイルが破損していることが原因の 1 つとして考えられます。

 **エラー ID:** BC30251

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. 型が別のプロジェクトまたは参照ファイル内にある場合は、プロジェクトまたはファイルを再インストールします。

2. 型が同じプロジェクト内にある場合は、型を含むアセンブリを再コンパイルします。

3. エラーがまだ発生する場合は、Visual Basic コンパイラを再インストールします。

4. エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。

## <a name="see-also"></a>関連項目

- [クラスとオブジェクト](../../programming-guide/language-features/objects-and-classes/index.md)
- [ご意見](/visualstudio/ide/feedback-options)
