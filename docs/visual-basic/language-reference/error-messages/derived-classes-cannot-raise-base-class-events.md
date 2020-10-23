---
title: 派生クラスで基本クラスのイベントを発生させることはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 7b86420466d77a6aa45b1201a9375b4433e4b5ec
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163442"
---
# <a name="bc30029-derived-classes-cannot-raise-base-class-events"></a>BC30029:派生クラスで基本クラスのイベントを発生させることはできません。

イベントを発生させることができるのは、それが宣言されている宣言領域からのみです。 そのため、クラスは、派生元のクラスであっても、他のクラスからイベントを発生させることはできません。

 **エラー ID:** BC30029

## <a name="to-correct-this-error"></a>このエラーを解決するには

- `Event` ステートメントまたは `RaiseEvent` ステートメントが同じクラス内になるように移動します。

## <a name="see-also"></a>関連項目

- [Event ステートメント](../statements/event-statement.md)
- [RaiseEvent ステートメント](../statements/raiseevent-statement.md)
