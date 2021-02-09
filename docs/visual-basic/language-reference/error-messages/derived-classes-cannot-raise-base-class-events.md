---
description: '詳細情報: BC30029:派生クラスで基本クラスのイベントを発生させることはできません。'
title: 派生クラスで基本クラスのイベントを発生させることはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 68546f2654f7c34fcb309d5af68e237d5f1eac79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796601"
---
# <a name="bc30029-derived-classes-cannot-raise-base-class-events"></a>BC30029:派生クラスで基本クラスのイベントを発生させることはできません。

イベントを発生させることができるのは、それが宣言されている宣言領域からのみです。 そのため、クラスは、派生元のクラスであっても、他のクラスからイベントを発生させることはできません。

 **エラー ID:** BC30029

## <a name="to-correct-this-error"></a>このエラーを解決するには

- `Event` ステートメントまたは `RaiseEvent` ステートメントが同じクラス内になるように移動します。

## <a name="see-also"></a>関連項目

- [Event ステートメント](../statements/event-statement.md)
- [RaiseEvent ステートメント](../statements/raiseevent-statement.md)
