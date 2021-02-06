---
description: 詳細については、「WCF でのセキュリティに関する考慮事項」をご覧ください。
title: WCF でのセキュリティの考慮事項
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: d75ff0d6eede4a46a5b795873e83445a04532993
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632478"
---
# <a name="security-considerations-in-wcf"></a>WCF でのセキュリティの考慮事項

このセクションのトピックでは、Windows Communication Foundation (WCF) アプリケーションを設計する際に考慮する必要があるさまざまなセキュリティ関連の項目を示します。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [情報漏えい](information-disclosure.md)  
 情報が開示または攻撃されるさまざまな方法、およびそれを軽減する方法について説明します。  
  
 [特権の昇格](elevation-of-privilege.md)  
 最初に付与されたものよりも高い承認アクセス許可を攻撃者に与えることの影響、およびそれを軽減する方法について説明します。  
  
 [サービス拒否](denial-of-service.md)  
 システムがメッセージを適切に処理できない場合の影響、およびそれを軽減する方法について説明します。  
  
 [改ざん](tampering.md)  
 メッセージの改ざんやメッセージの配信先の変更、およびそれを軽減する方法について説明します。  
  
 [リプレイ攻撃](replay-attacks.md)  
 攻撃者がメッセージのストリームを送受信者間でコピーし、そのストリームを 1 つ以上の第三者に対してリプレイすることによる影響、およびそれを軽減する方法について説明します。  
  
 [セキュリティで保護されたセッションに関するセキュリティの検討](security-considerations-for-secure-sessions.md)  
 セキュリティで保護されたセッションを実装する場合に、セキュリティに影響を及ぼす次の項目について説明します。  
  
 [サポートされていないシナリオ](unsupported-scenarios.md)  
 セキュリティの特定の側面がサポートされないため、避けたり配慮したりする必要のあるさまざまなシナリオを示します。  
  
## <a name="reference"></a>関連項目  

 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>関連項目  

 [セキュリティ ガイドラインとベスト プラクティス](security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a>関連項目

- [セキュリティ](security.md)
