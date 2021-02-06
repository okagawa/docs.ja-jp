---
description: '詳細情報: エンドポイント: 承認されていないセキュリティ呼び出し'
title: 'エンドポイント : 承認されていないセキュリティ呼び出し'
ms.date: 03/30/2017
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
ms.openlocfilehash: 258c984e8a7986594b6da6f5c2a8c030907f82ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655475"
---
# <a name="endpoint-security-calls-not-authorized"></a>エンドポイント : 承認されていないセキュリティ呼び出し

カウンター名 : 承認されていないセキュリティ呼び出し。  
  
## <a name="description"></a>説明  

 このカウンターは <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドで `false` が返された場合にインクリメントされます。 受信メッセージが有効なユーザーから適切な保護を適用して送信されたものであり、その一方でそのユーザーが特定のタスクの実行を許可されていないことを示します。
