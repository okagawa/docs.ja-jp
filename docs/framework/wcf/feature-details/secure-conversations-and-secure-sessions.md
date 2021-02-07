---
description: '詳細情報: セキュリティで保護されたメッセージ交換とセキュリティで保護されたセッション'
title: セキュリティ保護されたメッセージ交換とセッション
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
ms.openlocfilehash: dd935fd5de833dc2ba68b1aec3a2992dcba6a000
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733113"
---
# <a name="secure-conversations-and-secure-sessions"></a>セキュリティ保護されたメッセージ交換とセッション

Windows Communication Foundation (WCF) の機能は、相互に認証を行い、暗号化とデジタル署名のプロセスに同意する2つのエンドポイント間のセキュリティで保護されたセッションを確立する機能です。 たとえば、サービス エンドポイントは、クライアント エンドポイントに対して認証のために X.509 証明書に基づいたセキュリティ トークンを送信するよう要求する場合があります。 クライアントの認証が終わると、サービス エンドポイントはセキュリティ コンテキスト トークン (SCT: Security Context Token) をクライアントに返します。このセッションにおける後続のすべてのメッセージは、このセキュリティ トークンを使用してセキュリティ保護されます。 セキュリティで保護されたセッションが確立されると、SCT には対称キーが含まれるため、2 つのエンドポイント間で交換される一連のメッセージの効率が向上します。 X.509 証明書の基盤となる非対称キーでは、デジタル署名の生成やデータの暗号化を行う場合に、対称キーに比べて非常に大きな計算能力が必要になります。  
  
 ( [Ws-securitypolicy](https://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/ws-securitypolicy-1.2-spec-os.html) 標準のセクション6.2.7 で定義されている) ブートストラップポリシーには、チャネルをセキュリティで保護し、RST/SCT と RSTR/sct 交換の前にクライアントを認証するために使用されるメッセージセキュリティアサーションが含まれています。 特定の WCF 標準バインディングには、 `Security.Message.EstablishSecurityContext` セキュリティで保護されたメッセージ交換を使用するかどうかを制御するプロパティがあります。 カスタムバインドを使用する場合、ブートストラップは、 [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) 構成ファイル内で、またはコードでを呼び出すことによって、セキュリティバインド要素を入れ子にすることによって示され <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> ます。  
  
 セッションの詳細については、「 [セッションの使用](../using-sessions.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [セッション、インスタンス化、およびコンカレンシー](sessions-instancing-and-concurrency.md)
- [方法: セッションを必要とするサービスを作成する](how-to-create-a-service-that-requires-sessions.md)
