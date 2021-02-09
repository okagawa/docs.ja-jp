---
description: "詳細情報: BC31423:デリゲート型 '<eventname1>' および '<eventname2>' が一致しないため、イベント '<interface>' はインターフェイス '<delegate1>' 上のイベント '<delegate2>' を実装できません。"
title: デリゲート型 '<eventname1>' および '<eventname2>' が一致しないため、イベント '<interface>' はインターフェイス '<delegate1>' 上のイベント '<delegate2>' を実装できません。
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: cfb967d2b43ce1f34f56f3d019a9a663b000296c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796458"
---
# <a name="bc31423-event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a>BC31423:デリゲート型 '\<eventname1>' および '\<eventname2>' が一致しないため、イベント '\<interface>' はインターフェイス '\<delegate1>' 上のイベント '\<delegate2>' を実装できません。

イベントのデリゲート型が、インターフェイスのイベントのデリゲート型と一致しないため、Visual Basic ではイベントを実装できません。 このエラーは、インターフェイス内で複数のイベントを定義して、同じイベントと共にそれらを実装しようとする場合に、発生します。 実装されたすべてのイベントが `As` 構文を使用して宣言され、同じデリゲート型を指定する場合にのみ、イベントは 2 つ以上のイベントを実装することができます。

 **エラー ID:** BC31423

## <a name="to-correct-this-error"></a>このエラーを解決するには

- イベントを個別に実装します。

     または

- `As` 構文を使用してインターフェイスにイベントを定義し、同じデリゲート型を指定します。

## <a name="see-also"></a>関連項目

- [Event ステートメント](../statements/event-statement.md)
- [Delegate ステートメント](../statements/delegate-statement.md)
- [イベント](../../programming-guide/language-features/events/index.md)
