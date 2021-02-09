---
description: '詳細情報: エラーが発生していないときに Resume を実行することはできません。'
title: エラーが発生していないときに Resume を実行することはできません。
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: a2284484be65ae975c6e09499ec19e3cfd8d4a04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792012"
---
# <a name="resume-without-error"></a>エラーが発生していないときに Resume を実行することはできません。

`Resume` ステートメントがエラー処理コードの外側に記述されていたか、エラーが発生していない場合でもコードがエラー ハンドラーにジャンプしました。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. `Resume` ステートメントをエラー ハンドラー内に移動するか、または削除します。  
  
2. プロシージャ間でラベルにジャンプすることはできないため、プロシージャでエラー ハンドラーを識別するラベルを検索します。 `On Error GoTo` ステートメントではない `GoTo` ステートメントのターゲットとして重複するラベルが指定されている場合は、その目的のターゲットと一致するように行ラベルを変更します。  
  
## <a name="see-also"></a>関連項目

- [Resume ステートメント](../statements/resume-statement.md)
- [On Error ステートメント](../statements/on-error-statement.md)
