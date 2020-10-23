---
title: "'<eventname>' はイベントであるため、直接呼び出すことはできません。"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 246cb92daa2c838c95f695542f33cf02af42764d
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161986"
---
# <a name="bc32022-eventname-is-an-event-and-cannot-be-called-directly"></a>BC32022: '\<eventname>' はイベントであるため、直接呼び出すことはできません

'<`eventname`>' はイベントであるため、直接呼び出すことはできません。 `RaiseEvent` ステートメントを使用して、イベントを発生させます。

 プロシージャ呼び出しは、プロシージャ名のイベントを指定します。 イベント ハンドラーはプロシージャですが、イベント自体はシグナル通知デバイスであり、これを発生させて処理する必要があります。

 **エラー ID:** BC32022

## <a name="to-correct-this-error"></a>このエラーを解決するには

- `RaiseEvent` ステートメントを使用して、イベントを通知し、それを処理するプロシージャを呼び出します。

## <a name="see-also"></a>関連項目

- [RaiseEvent ステートメント](../statements/raiseevent-statement.md)
