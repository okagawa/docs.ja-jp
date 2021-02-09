---
description: "詳細情報: BC32022: '<eventname>' はイベントであるため、直接呼び出すことはできません"
title: "'<eventname>' はイベントであるため、直接呼び出すことはできません。"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: f9d4b8fe54e1101e7963933f871cf5af2c1af903
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796445"
---
# <a name="bc32022-eventname-is-an-event-and-cannot-be-called-directly"></a>BC32022: '\<eventname>' はイベントであるため、直接呼び出すことはできません

'<`eventname`>' はイベントであるため、直接呼び出すことはできません。 `RaiseEvent` ステートメントを使用して、イベントを発生させます。

 プロシージャ呼び出しは、プロシージャ名のイベントを指定します。 イベント ハンドラーはプロシージャですが、イベント自体はシグナル通知デバイスであり、これを発生させて処理する必要があります。

 **エラー ID:** BC32022

## <a name="to-correct-this-error"></a>このエラーを解決するには

- `RaiseEvent` ステートメントを使用して、イベントを通知し、それを処理するプロシージャを呼び出します。

## <a name="see-also"></a>関連項目

- [RaiseEvent ステートメント](../statements/raiseevent-statement.md)
