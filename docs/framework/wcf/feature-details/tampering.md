---
description: '詳細情報: 改ざん'
title: 改ざん
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 3b14fef66e5c98737d8d2f6a8b889f16c83020f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793325"
---
# <a name="tampering"></a>改ざん

*改ざん* とは、メッセージを変更したり、メッセージの配信を行ったり、変更されたメッセージを目的以外の目的で使用したりする行為です。  
  
## <a name="do-not-disable-ws-addressing"></a>WS-Addressing を無効にしない  

 WS-Addressing の仕様では、各メッセージにアドレス ヘッダーが提供されるため、メッセージの受信者はメッセージの送信者を検証できます。 この機能を無効にするには、<xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> プロパティを <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> に設定します。  
  
 セキュリティ モードが Message に設定された状態で、WS-Addressing が無効になっていると、攻撃者がクライアントから要求を取得して、これを別のサービスに送信した場合、要求を受信したサービスは、このメッセージが元のクライアントから送信されたことを検出できません。 事実上、最初のサービスは、2 番目のサービスと対話するときに、自分をクライアントと偽ることができます。  
  
 これを防ぐには、<xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> プロパティを絶対に <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> に設定しないようにし、静的 <xref:System.ServiceModel.Channels.MessageVersion> プロパティのように、<xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> プロパティを <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> に設定する <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> の使用を避けます。  
  
## <a name="see-also"></a>関連項目

- [セキュリティに関する考慮事項](security-considerations-in-wcf.md)
- [情報漏えい](information-disclosure.md)
- [特権の昇格](elevation-of-privilege.md)
- [サービス拒否](denial-of-service.md)
- [サポートされていないシナリオ](unsupported-scenarios.md)
- [リプレイ攻撃](replay-attacks.md)
