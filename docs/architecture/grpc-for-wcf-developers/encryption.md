---
title: 暗号化とネットワークセキュリティ-WCF 開発者向けの gRPC
description: GRPC でのネットワークセキュリティと暗号化に関する注意事項
ms.date: 01/06/2021
ms.openlocfilehash: cf4d30ff862e64aadfeacf45ed3768fc14737800
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970142"
---
# <a name="encryption-and-network-security"></a>暗号化とネットワークセキュリティ

Windows Communication Foundation (WCF) のネットワークセキュリティモデルは広範で複雑です。 これには、HTTPS または TLS over TCP を使用したトランスポートレベルのセキュリティと、個々のメッセージを暗号化するための WS-Security 仕様を使用したメッセージレベルのセキュリティが含まれます。

gRPC は、基盤となる HTTP/2 プロトコルにセキュリティで保護されたネットワークを残し、TLS 証明書を使用してセキュリティで保護することができます。

Web ブラウザーは、HTTP/2 の TLS 接続を使用することを主張していますが、を含むほとんどのプログラム用クライアントです。NET は `HttpClient` 、暗号化されていない接続を介して HTTP/2 を使用できます。

パブリック Api の場合、TLS 接続を常に使用し、適切な SSL 機関からサービスに有効な証明書を提供する必要があります。 この[暗号化](https://letsencrypt.org)は、無料の自動 SSL 証明書を提供します。ほとんどのホスティングインフラストラクチャでは、一般的なプラグインまたは拡張機能を使用して、標準のプラグインまたは拡張機能をサポートしています。

企業ネットワーク全体の内部サービスについても、TLS を使用して、gRPC サービスとの間のネットワークトラフィックをセキュリティで保護することを検討する必要があります。

Kubernetes で実行されているサービス間で明示的な TLS を使用する必要がある場合は、クラスター内証明機関と、 [cert](https://docs.cert-manager.io/en/latest/)manager のような証明書マネージャーコントローラーの使用を検討してください。 展開時に、サービスに証明書を自動的に割り当てることができます。

>[!div class="step-by-step"]
>[前へ](channel-credentials.md)
>[次へ](grpc-in-production.md)
