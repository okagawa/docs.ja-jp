---
description: 詳細については、使用する目的と標準に基づいた WCF への ASP.NET ウェブサービスの比較に関するページを参照してください。
title: 使用目的と使用標準に基づく ASP.NET Web サービスと WCF との比較
ms.date: 03/30/2017
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
ms.openlocfilehash: debc20f3ab3e8e9f83641eaa7d3b52dabe82055c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743448"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a>使用目的と使用標準に基づく ASP.NET Web サービスと WCF との比較

ASP.NET Web サービスは、HTTP 上で SOAP (Simple Object Access Protocol) を使用してメッセージを送受信するアプリケーションを構築するために開発されました。 メッセージ構造は XML スキーマを使用して定義できます。また、.NET Framework オブジェクトに対するメッセージのシリアル化を容易にするツールも提供されています。 このテクノロジを使用すると、Web サービス記述言語 (WSDL) で Web サービスを記述するメタデータが自動で生成されます。また、WSDL から Web サービス用のクライアントを生成する別のツールも用意されています。  
  
 WCF は、.NET Framework アプリケーションが他のソフトウェアエンティティとメッセージを交換できるようにするためのものです。 既定では SOAP が使用されますが、任意の形式のメッセージを使用でき、任意のトランスポート プロトコルを使用してメッセージを伝達できます。 メッセージ構造は XML スキーマを使用して定義できます。また、.NET Framework オブジェクトに対するメッセージをシリアル化するさまざまなオプションがあります。 WCF は、WSDL のテクノロジを使用して構築されたアプリケーションを記述するメタデータを自動的に生成できます。また、これらのアプリケーションのクライアントを WSDL から生成するためのツールも提供します。  
  
 ASP.NET ウェブサービスでサポートされる標準は、 [ASP.NET を使用して作成された XML Web サービスの利点](/previous-versions/dotnet/netframework-4.0/0859ebft(v=vs.100))に関するドキュメントに記載されています。 WCF でサポートされる標準の詳細な一覧については、 [「System-Provided 相互運用性バインドでサポートされる Web サービスプロトコル](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [開発者の視点から見た ASP.NET Web サービスと WCF との比較](comparing-aspnet-web-services-to-wcf-based-on-development.md)
