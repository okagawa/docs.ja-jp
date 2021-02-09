---
description: '詳細情報: オートメーション エラーです。'
title: オートメーション エラーです。
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: e4d283b16b4c54e2488fedfc58d3c881cf6b0218
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797121"
---
# <a name="automation-error"></a>オートメーション エラーです。

メソッドの実行中、またはオブジェクト変数のプロパティの取得中または設定中にエラーが発生しました。 エラーは、オブジェクトを作成したアプリケーションによって報告されました。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. `Err` オブジェクトのプロパティをチェックし、エラーの原因と性質を確認します。  
  
2. アクセス ステートメントの直前で `On Error Resume Next` ステートメントを使用し、アクセス ステートメントの直後のエラーを確認します。  
  
## <a name="see-also"></a>関連項目

- [エラーの種類](../../programming-guide/language-features/error-types.md)
- [ご意見](/visualstudio/ide/feedback-options)
