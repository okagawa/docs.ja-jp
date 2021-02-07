---
description: 詳細については、Web サービスプロトコルの相互運用性に関するガイドを参照してください。
title: Web サービスプロトコルの相互運用性ガイド
ms.date: 03/30/2017
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
ms.openlocfilehash: cab744818d3a52c6f6cd0d95195d9112ac9babf6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752549"
---
# <a name="web-services-protocols-interoperability-guide"></a>Web サービスプロトコルの相互運用性ガイド

Windows Communication Foundation (WCF) は、多くの Web サービスプロトコルを実装します。 これらのプロトコルの多くには、さまざまなオプションと拡張ポイントが用意されており、それらの実装は実装者の裁量に任されています。 この記事では、WCF が実装する Web サービスプロトコルの一覧を示します。 このセクション内の他の記事では、サポートされている各プロトコルの実装の詳細について説明します。

## <a name="web-services-protocols-implemented-by-wcf"></a>WCF によって実装された Web サービスプロトコル

WCF では、コントラクト機能を通じて、チャネルと Web サービスアプリケーションプロトコルを介して Web サービス (WS) インフラストラクチャプロトコルがサポートされます。 アプリケーション プロトコルの相互運用性は、XML スキーマ記述言語 (XSD) 1.0 と Web サービス記述言語 (WSDL) 1.1 を通じて実現されます。

インフラストラクチャ プロトコルの相互運用性は、WS-* 仕様によって提供されます。 WCF チャネルは、さまざまな WS-MANAGEMENT プロトコルをサポート \* しています。 WCF チャネルは、バインド要素を使用して構成されます。 次の表には、 \* さまざまな WCF バインド要素によって実装される ws-policy プロトコルの完全な一覧が含まれています。

<xref:System.ServiceModel.Channels.HttpTransportBindingElement> は、次の表の仕様をサポートします。

|仕様/ドキュメント|リンク|
|-----------------------------|----------|
|HTTP 1.1|[RFC 2616](https://www.rfc-editor.org/rfc/rfc2616.txt)|
|SOAP 1.1 HTTP バインディング|[Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)、セクション7|
|SOAP 1.2 HTTP バインディング|[SOAP バージョン1.2 パート 2: Adjuncts (Second Edition)](https://www.w3.org/TR/soap12-part2/)、セクション7|

<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> および <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> は、次の表の仕様をサポートします。

|仕様/ドキュメント|リンク|
|-----------------------------|----------|
|XML|[Extensible Markup Language (XML) 1.0 (Fourth Edition)](https://www.w3.org/TR/REC-xml/)|
|SOAP 1.1|[Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)|
|SOAP 1.2 コア|[SOAP Version 1.2 Part 1: Messaging Framework (Second Edition)](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)|
|WS-Addressing 2004/08|[Web Services Addressing (WS-Addressing)](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)|
|W3C Web Services Addressing 1.0 - コア|[Web Services Addressing 1.0 - Core](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509/)|
|W3C Web Services Addressing 1.0 - SOAP バインディング|[Web Services Addressing 1.0 - SOAP Binding](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509/)|
|W3C Web Services Addressing 1.0 - WSDL バインディング*|[Web Services Addressing 1.0 - WSDL Binding](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)|
|W3C Web Services Addressing 1.0 - メタデータ|[Web Services Addressing 1.0 - Metadata](https://www.w3.org/TR/ws-addr-metadata/)|
|WSDL SOAP1.1 バインディング|[Web Services Description Language (WSDL) 1.1](https://www.w3.org/TR/wsdl/)|
|WSDL SOAP1.2 バインディング|[WSDL 1.1 Binding Extension for SOAP 1.2](https://www.w3.org/Submission/wsdl11soap12/)|

<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> は、次の表の仕様をサポートします。

|仕様/ドキュメント|リンク|
|-----------------------------|----------|
|XOP|[XML-binary Optimized Packaging](https://www.w3.org/TR/xop10/)|
|MTOM + SOAP1.2 バインディング|[SOAP Message Transmission Optimization Mechanism](https://www.w3.org/TR/soap12-mtom/)|
|MTOM SOAP 1.1 バインディング|[SOAP 1.1 Binding for MTOM 1.0](https://www.w3.org/Submission/soap11mtom10/)|
|MTOM WS-Policy アサーション|[MTOM シリアル化ポリシーアサーション (MTOMPolicy)](https://www.w3.org/Submission/WS-MTOMPolicy/)|

<xref:System.ServiceModel.Channels.SecurityBindingElement> は、次の表の仕様をサポートします。

|仕様/ドキュメント|リンク|
|-----------------------------|----------|
|WSS SOAP Message Security 1.0|[Web Services Security: SOAP メッセージセキュリティ1.0](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)|
|WSS: Username Token Profile 1.0|[Web Services Security UsernameToken Profile 1.0](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> 必須 Password/@Type = passwordtext (既定値)|
|WSS: X.509 Token Profile 1.0|[Web Services Security X.509 Certificate Token Profile](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)|
|WSS: SAML 1.1 Token Profile 1.0|[Web Services Security: SAML Token Profile](https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf)|
|WSS SOAP Message Security 1.1|[Web Services Security: SOAP Message Security 1.1](https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf)|
|WSS Username Token Profile 1.1|[Web Services Security UsernameToken Profile 1.1](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> パスワード ベースのキー派生は実装していません。<br /><br /> 必須 Password/@Type = passwordtext (既定値)|
|WSS: X509 Token Profile 1.1|[Web Services Security X.509 Certificate Token Profile 1.1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)|
|WSS: Kerberos Token Profile 1.1|[Web Services Security Kerberos Token Profile 1.1](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)|
|WSS: SAML 1.1 Token Profile 1.1|[Web Services Security SAML Token Profile 1.1](https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf)|
|WS-SecureConversation|[Web Services Secure Conversation Language](http://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)|
|WS-Trust 1.4|[Web Services Trust Language](https://docs.oasis-open.org/ws-sx/ws-trust/200802)|
|WS-SecurityPolicy 2005/07|[Web Services Secure Conversation Language](http://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> OASIS WS-SX 技術委員会に提出された正誤表で修正されています。<br /><br /> [ws-sx message](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html)|
|WS-ReliableMessaging 1.1|[信頼できるメッセージング プロトコル バージョン 1.1](reliable-messaging-protocol-version-1-1.md)|

<xref:System.ServiceModel.Channels.TransactionFlowBindingElement> は、次の表の仕様をサポートします。

|仕様/ドキュメント|リンク|
|-----------------------------|----------|
|WS-Coordination|[Web Services Coordination](/previous-versions/ms951231(v=msdn.10))|
|WS-AtomicTransaction|[Web Services Atomic Transaction](http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)|

<xref:System.ServiceModel.Description.MetadataExporter>、<xref:System.ServiceModel.Description.MetadataImporter>、<xref:System.ServiceModel.Description.WsdlExporter>、<xref:System.ServiceModel.Description.WsdlImporter>、および <xref:System.ServiceModel.Description.MetadataResolver> の各クラスは、次のメタデータ仕様をサポートします。

- [XML Schema Part 1: Structures Second Edition](https://www.w3.org/TR/xmlschema-1/)

- [XML Schema Part 2: Data types Second Edition](https://www.w3.org/TR/xmlschema-2/)

- [WSDL 1.1](https://www.w3.org/TR/wsdl/)

- [WS-POLICY 1.2](https://www.w3.org/Submission/2006/SUBM-WS-Policy-20060425/)

- [WS-Policy 1.5](https://www.w3.org/TR/ws-policy/)

- [WS-PolicyAttachment 1.2](https://www.w3.org/Submission/2006/SUBM-WS-PolicyAttachment-20060425/)

- [WS-MetadataExchange 1.1](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)

- [メタデータ取得のための WS-Transfer Get ](https://www.w3.org/Submission/2006/SUBM-WS-Transfer-20060315/)

さらに、次の相互運用性プロファイルが WCF 全体に実装されます。

- [Basic Profile 1.1](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html)

- [Simple SOAP Binding 1.0](http://www.ws-i.org/Profiles/SimpleSoapBindingProfile-1.0-2004-08-24.html)

- [Basic Security Profile 1.0 ワーキング ドラフト](http://www.ws-i.org/Profiles/BasicSecurityProfile-1.0-2006-03-29.html)

## <a name="see-also"></a>関連項目

- [システム標準の相互運用性バインディングがサポートしている Web サービス プロトコル](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [メッセージング プロトコル](messaging-protocols.md)
- [データ コントラクト スキーマの参照](data-contract-schema-reference.md)
- [WSDL とポリシー](wsdl-and-policy.md)
- [セキュリティ プロトコル](security-protocols.md)
- [信頼できるメッセージング プロトコル バージョン 1.0](reliable-messaging-protocol-version-1-0.md)
- [信頼できるメッセージング プロトコル バージョン 1.1](reliable-messaging-protocol-version-1-1.md)
- [トランザクション プロトコル](transaction-protocols.md)
- [コンテキスト交換プロトコル](context-exchange-protocol.md)
