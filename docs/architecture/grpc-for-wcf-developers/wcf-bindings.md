---
title: Wcf のバインディングとトランスポート-WCF 開発者向け gRPC
description: さまざまな WCF バインドとトランスポートが gRPC とどのように比較されるかについて説明します。
ms.date: 12/15/2020
ms.openlocfilehash: 7a50e3e4468d86a6140066502a765818119642d4
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938508"
---
# <a name="wcf-bindings-and-transports"></a>WCF のバインドとトランスポート

Windows Communication Foundation (WCF) には、さまざまなネットワークプロトコル、ワイヤ形式、およびその他の実装の詳細を指定する組み込み *バインド* があります。 gRPC には、ネットワークプロトコルとワイヤ形式が1つだけあります。 (技術的にはワイヤ形式をカスタマイズ *でき* ますが、これはこの書籍の範囲を超えています)。GRPC はほとんどの場合、最適なソリューションを提供していることがわかっているでしょう。

ここでは、最も関連性の高い WCF バインドについて簡単に説明し、gRPC で同等のバインドと比較する方法を示します。

## <a name="nettcp"></a>Wcf-nettcp

WCF の NetTCP バインディングを使用すると、永続的な接続、小さいメッセージ、および双方向のメッセージングを実現できます。 ただし、.NET クライアントとサーバーの間でのみ機能します。 gRPC では同じ機能を使用できますが、複数のプログラミング言語とプラットフォームでサポートされています。

gRPC には WCF の NetTCP バインドの多くの機能がありますが、常に同じ方法で実装されるわけではありません。 たとえば、WCF では、暗号化は構成によって制御され、フレームワークで処理されます。 GRPC では、TLS 経由で HTTP/2 を介して接続レベルで暗号化が行われます。

## <a name="http"></a>HTTP

通常、BasicHttpBinding という WCF バインディングはテキストベースで、ワイヤ形式として SOAP を使用します。 NetTCP バインドと比べて低速です。 クロスプラットフォームの相互運用性、またはインターネットインフラストラクチャ経由の接続を提供するために使用されます。

GRPC では、メッセージのバイナリ Protobuf ワイヤ形式を使用して、基になるトランスポート層として HTTP/2 を使用します。 これにより、すべての最新のプログラミング言語とフレームワークを使用して、NetTCP サービスレベルのパフォーマンスと完全なクロスプラットフォームの相互運用性を実現できます。

## <a name="named-pipes"></a>名前付きパイプ

WCF は、同じ物理マシン上のプロセス間の通信に使用する *名前付きパイプ* のバインドを提供しました。 ASP.NET Core gRPC の最初のリリースでは、名前付きパイプはサポートされていません。 名前付きパイプ (および Unix ドメインソケット) のクライアントとサーバーのサポートを追加することは、将来のリリースの目的です。

## <a name="msmq"></a>MSMQ

MSMQ は専用の Windows メッセージキューです。 WCF による MSMQ へのバインドを使用すると、将来、いつでも処理される可能性があるクライアントからの "火災および忘れる" 要求を行うことができます。 gRPC では、メッセージキュー機能はネイティブには提供されません。

代替手段として、Azure Service Bus、RabbitMQ、Kafka などのメッセージングシステムを直接使用することをお勧めします。 この機能は、クライアントがメッセージをキューに直接配置するか、メッセージをキューに入れる gRPC クライアントストリーミングサービスを使用して実装できます。

## <a name="webhttpbinding"></a>WebHttpBinding

WebHttpBinding (WCF REST とも呼ばれます) では、属性と属性を使用することに `WebGet` `WebInvoke` より、この動作があまり一般的ではないときに JSON を読み上げることができる RESTful api を開発できます。 WCF REST でビルドされた RESTful API を使用している場合は、通常の ASP.NET Core MVC Web API アプリケーションに移行することを検討してください。 この移行では、gRPC への変換と同じ機能が提供されます。

>[!div class="step-by-step"]
>[前へ](wcf-endpoints-grpc-methods.md)
>[次へ](rpc-types.md)
