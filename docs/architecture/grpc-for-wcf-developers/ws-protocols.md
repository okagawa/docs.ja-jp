---
title: WS-* プロトコル-WCF 開発者向け gRPC
description: WCF でサポートされている WS-* プロトコルと gRPC で使用可能な代替方法の確認
author: markrendle
ms.date: 12/15/2020
ms.openlocfilehash: d6fffdd5153c799c78ad949a3b16fa72e9612e43
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938482"
---
# <a name="ws--protocols"></a>\*プロトコル

Windows Communication Foundation (WCF) を使用する利点の1つは、既存の _WS \*_ 標準プロトコルの多くをサポートすることでした。 このセクションでは、gRPC によって同じプロトコルがどのように管理されるか \* について簡単に説明し、代替手段がない場合に使用できるオプションについて説明します。

## <a name="metadata-exchange-ws-policy-ws-discovery-and-so-on"></a>メタデータ交換: WS-POLICY、WS-I Discovery など

SOAP サービスでは、Web サービス記述言語 (WSDL) スキーマドキュメントが、データ形式、操作、通信オプションなどの情報と共に公開されます。 このスキーマを使用して、クライアントコードを生成できます。

gRPC は、サーバーとクライアントが同じファイルから生成された場合に最適に機能し `.proto` ますが、サーバーリフレクションオプションの拡張機能を使用すると、実行中のサーバーから動的な情報を公開することができます。 詳細については、「 [grpc. リフレクション](https://nuget.org/packages/Grpc.Reflection) NuGet パッケージ」および「 [Grpc C# サーバーリフレクション](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) 」を参照してください。

WS-Discovery プロトコルは、ローカルネットワーク上のサービスを検索するために使用されます。 gRPC サービスは、DNS または Consul や飼育係などのサービスレジストリを使用して配置されます。

## <a name="security-ws-security-ws-federation-xml-encryption-and-so-on"></a>セキュリティ: WS-SECURITY、WS-FEDERATION、XML 暗号化、その他

セキュリティ、認証、および承認の詳細については、 [第6章](security.md)を参照してください。 ただし、WCF とは異なり、gRPC は WS-SECURITY、WS-FEDERATION、または XML 暗号化をサポートしていないことに注意してください。 それでも、gRPC は優れたセキュリティを提供しています。 すべての gRPC ネットワークトラフィックは、HTTP/2 over TLS を使用しているときに自動的に暗号化されます。 相互クライアント/サーバー認証には X509 証明書を使用できます。

## <a name="ws-reliablemessaging"></a>WS-ReliableMessaging

gRPC では、ws-reliablemessaging に相当するものは提供されません。 再試行のセマンティクスは、コードで処理する必要があります [。たとえば](https://github.com/App-vNext/Polly)、通常のようなライブラリを使用します。 Kubernetes または同様のオーケストレーション環境で実行されている場合、 [サービスメッシュ](service-mesh.md) はサービス間の信頼性の高いメッセージングを提供するのにも役立ちます。

## <a name="ws-transaction-ws-coordination"></a>WS-ATOMICTRANSACTION、WS-Coordination

WCF による分散トランザクションの実装では、Microsoft 分散トランザクションコーディネーター (MSDTC) を使用します。 これは、SQL Server、MSMQ、Windows ファイルシステムなど、特にサポートされているリソースマネージャーと連携します。 現在のマイクロサービスの世界では、使用されているテクノロジの範囲が広いため、まだ同等のものはありません。 トランザクションの詳細については、「 [付録 a](appendix.md)」を参照してください。

>[!div class="step-by-step"]
>[前へ](error-handling.md)
>[次へ](migrate-wcf-to-grpc.md)
