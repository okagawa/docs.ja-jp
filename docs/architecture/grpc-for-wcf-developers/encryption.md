---
title: 暗号化とネットワークセキュリティ-WCF 開発者向けの gRPC
description: GRPC でのネットワークセキュリティと暗号化に関する注意事項
ms.date: 12/15/2020
ms.openlocfilehash: 0735158ed69ce425c4f00eed6c42689b888a1885
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938625"
---
# <a name="encryption-and-network-security"></a>暗号化とネットワークセキュリティ

Windows Communication Foundation (WCF) のネットワークセキュリティモデルは広範で複雑です。 これには、HTTPS または TLS over TCP を使用したトランスポートレベルのセキュリティと、個々のメッセージを暗号化するための WS-Security 仕様を使用したメッセージレベルのセキュリティが含まれます。

gRPC は、基盤となる HTTP/2 プロトコルにセキュリティで保護されたネットワークを残し、TLS 証明書を使用してセキュリティで保護することができます。

Web ブラウザーは、HTTP/2 の TLS 接続を使用することを主張していますが、を含むほとんどのプログラム用クライアントです。NET は `HttpClient` 、暗号化されていない接続を介して HTTP/2 を使用できます。 `HttpClient` 既定では暗号化が必要ですが、スイッチを使用してこの動作をオーバーライドでき <xref:System.AppContext> ます。

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

パブリック Api の場合、TLS 接続を常に使用し、適切な SSL 機関からサービスに有効な証明書を提供する必要があります。 この[暗号化](https://letsencrypt.org)は、無料の自動 SSL 証明書を提供します。ほとんどのホスティングインフラストラクチャでは、一般的なプラグインまたは拡張機能を使用して、標準のプラグインまたは拡張機能をサポートしています。

企業ネットワーク全体の内部サービスについても、TLS を使用して、gRPC サービスとの間のネットワークトラフィックをセキュリティで保護することを検討する必要があります。

Kubernetes で実行されているサービス間で明示的な TLS を使用する必要がある場合は、クラスター内証明機関と、 [cert](https://docs.cert-manager.io/en/latest/)manager のような証明書マネージャーコントローラーの使用を検討してください。 展開時に、サービスに証明書を自動的に割り当てることができます。

>[!div class="step-by-step"]
>[前へ](channel-credentials.md)
>[次へ](grpc-in-production.md)
