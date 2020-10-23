---
title: 型 '<typename>' にはコンストラクターがありません。
ms.date: 07/20/2015
f1_keywords:
- bc30251
- vbc30251
helpviewer_keywords:
- BC30251
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
ms.openlocfilehash: 249bcb7020f26c7c43d560e91ef7a34e4dc64470
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161180"
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
