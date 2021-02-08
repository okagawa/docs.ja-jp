---
description: '詳細情報: インスタンス完了アクション'
title: インスタンス完了アクション
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 84405ca9869369e4fe00b0049d628671a79a9f68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792688"
---
# <a name="instance-completion-action"></a>インスタンス完了アクション

SQL Workflow Instance Store の **インスタンス完了アクション** プロパティを使用すると、インスタンスの完了後にワークフローインスタンスのデータとメタデータを永続性データベースから削除するかどうかを指定できます。 このプロパティに指定できる値は、 **DeleteAll** および **DeleteNothing** です。 これらのオプションについて次の一覧で説明します。

- **DeleteAll (既定)。** このプロパティの値を DeleteAll に設定すると、ワークフロー インスタンスの完了後に、永続性データベースからワークフロー インスタンスのデータおよびメタデータは削除されます。

- **DeleteNothing。** このプロパティの値を DeleteNothing に設定すると、ワークフロー インスタンスが完了しても、ワークフロー インスタンスのデータおよびメタデータは永続性データベースに残ります。

  > [!CAUTION]
  > インスタンスの完了後にインスタンス状態情報を残すと、永続性データベースのサイズが大きくなります。 データベースのサイズが大きくなるにつれて、永続性サブシステムが実行するデータベース操作にかかる時間が長くなります。そのため、永続性データベースからインスタンス状態情報を定期的に削除して、パフォーマンスの要件を満たすレベルでサービスが実行されるようにします。
