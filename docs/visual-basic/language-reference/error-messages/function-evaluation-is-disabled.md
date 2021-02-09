---
description: '詳細情報: BC30957:前の関数の評価がタイムアウトしたため、関数の評価は無効になりました。'
title: 前の関数の評価がタイムアウトしたため、関数の評価は無効になりました。
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: 32e4b460a0334a542d59091bfc0b9a2337fdd089
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796185"
---
# <a name="bc30957-function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>BC30957:前の関数の評価がタイムアウトしたため、関数の評価は無効になりました。

前の関数の評価がタイムアウトしたため、関数の評価は無効になりました。関数の評価をもう一度有効にするには、もう一度ステップを実行するか、またはデバッグを再起動してください。

 Visual Studio デバッガーで、プロシージャ呼び出しが式に指定されていますが、別の評価がタイムアウトしています。

 プロシージャ呼び出しがタイム アウトした原因には、*無限ループ* などが考えられます。 詳細については、「[For...Next ステートメント](../statements/for-next-statement.md)」を参照してください。

 無限ループの特殊なケースが *再帰* です。 詳細については、「[再帰プロシージャ](../../programming-guide/language-features/procedures/recursive-procedures.md)」を参照してください。

 **エラー ID:** BC30957

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. 可能であれば、前回の関数の評価がどれかを判断し、タイムアウトした理由を調べます。判断できない場合、このエラーが再度表示される可能性があります。

2. デバッガーのステップをもう一度実行するか、デバッガーを終了させて再起動します。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデバッグ](/visualstudio/debugger/debugger-feature-tour)
- [デバッガーでのコード間の移動](/visualstudio/debugger/navigating-through-code-with-the-debugger)
