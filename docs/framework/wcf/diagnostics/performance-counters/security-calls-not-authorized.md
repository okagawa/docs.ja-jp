---
title: 承認されていないセキュリティ呼び出し
ms.date: 03/30/2017
ms.assetid: cb6acdcd-7336-42e1-9ae8-ac891336cd58
ms.openlocfilehash: 5575b108353e9c434ff01e76edc127e8691f0bf4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276127"
---
# <a name="security-calls-not-authorized"></a>承認されていないセキュリティ呼び出し

カウンター名 : 承認されていないセキュリティ呼び出し。  
  
## <a name="description"></a>Description  

 このカウンターは <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドで `false` が返された場合にインクリメントされます。 受信メッセージが有効なユーザーから適切な保護を適用して送信されたものであり、その一方でそのユーザーが特定のタスクの実行を許可されていないことを示します。
