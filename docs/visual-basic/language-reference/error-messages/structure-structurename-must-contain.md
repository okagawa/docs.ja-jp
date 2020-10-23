---
title: 構造体 '<structurename>' は少なくとも 1 つのインスタンス メンバー変数、または 'Custom' に設定されていない少なくとも 1 つのインスタンス イベント宣言を含まなければなりません。
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 4e7ef82659c43be08ee444eaf3f4df663f7aaa53
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159652"
---
# <a name="bc30941-structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a>BC30941:構造体 '\<structurename>' は少なくとも 1 つのインスタンス メンバー変数、または 'Custom' に設定されていない少なくとも 1 つのインスタンス イベント宣言を含まなければなりません。

構造体の定義には、非共有の変数または非共有の非カスタム イベントは含まれません。

 すべての構造体には、すべてのインスタンスに対して集合的に ([Shared](../modifiers/shared.md)) ではなく、特定の各インスタンスに対して (非共有) 適用される変数またはイベントが含まれている必要があります。 非共有の定数、プロパティ、およびプロシージャは、この要件を満たしていません。 さらに、非共有の変数がなく、1 つの非共有イベントのみが存在する場合、そのイベントを `Custom` イベントにすることはできません。

 **エラー ID:** BC30941

## <a name="to-correct-this-error"></a>このエラーを解決するには

- `Shared` ではない変数またはイベントを少なくとも 1 つ定義します。 イベントを 1 つだけ定義する場合、非共有にするだけでなく、非カスタムにする必要があります。

## <a name="see-also"></a>関連項目

- [構造体](../../programming-guide/language-features/data-types/structures.md)
- [方法: 構造体を宣言する](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Structure ステートメント](../statements/structure-statement.md)
