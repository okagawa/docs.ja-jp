---
description: "詳細情報: BC42104:変数 '<variablename>' は、値が割り当てられる前に参照によって使用されています。"
title: 変数 '<variablename>' は、値が割り当てられる前に参照によって使用されています。
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 501c3e3971c5ca0ebdba6981134f5029b77d0075
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701496"
---
# <a name="bc42104-variable-variablename-is-used-before-it-has-been-assigned-a-value"></a>BC42104:変数 '\<variablename>' は、値が割り当てられる前に参照によって使用されています。

変数 '\<variablename>' は、値が割り当てられる前に使用されています。 結果として、実行時に null 参照の例外が発生する可能性があります。

 アプリケーションには、値が割り当てられる前に変数を読み取るコードを通る可能性があるパスが少なくとも 1 つあります。

 変数に値が割り当てられていない場合、変数はそのデータ型の既定値を保持します。 参照データ型の場合、その既定値は [Nothing](../nothing.md)です。 値が `Nothing` である参照変数を読み取ると、状況によって <xref:System.NullReferenceException> が発生する可能性があります。

 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。

 **エラー ID:** BC42104

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 制御フロー ロジックをチェックして、変数を読み取るステートメントに制御が渡される前に、変数に有効な値が設定されていることを確認します。

- 変数が常に有効な値を持つようにする 1 つの方法は、その宣言の一部として変数を初期化することです。 [Dim ステートメント](../statements/dim-statement.md)の "初期化" に関する説明を参照してください。

## <a name="see-also"></a>関連項目

- [Dim ステートメント](../statements/dim-statement.md)
- [変数宣言](../../programming-guide/language-features/variables/variable-declaration.md)
- [変数のトラブルシューティング](../../programming-guide/language-features/variables/troubleshooting-variables.md)
