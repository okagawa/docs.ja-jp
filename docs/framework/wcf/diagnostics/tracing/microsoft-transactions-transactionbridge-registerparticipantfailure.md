---
description: 詳細については、RegisterParticipantFailure を参照してください。
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: e930ee66720a9f397999d729e8d680fce9a37e29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99770626"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a>Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure

WS-AT プロトコル サービスは、制御プロトコルの参加要素の登録に失敗しました。  
  
## <a name="description"></a>説明  

 MSDTC により無効な登録要求が検出された場合にトレースされます。 これは、複数の完了登録要求や内部エラーによって発生することがあります。  
  
## <a name="troubleshooting"></a>トラブルシューティング  

 完了を複数回登録しないでください。  また、トレース メッセージ内のステータス文字列を調べて、アクション可能な項目が存在するかどうかを確認します。  
  
## <a name="see-also"></a>関連項目

- [トレース](index.md)
- [トレースを使用したアプリケーションのトラブルシューティング](using-tracing-to-troubleshoot-your-application.md)
- [管理と診断](../index.md)
