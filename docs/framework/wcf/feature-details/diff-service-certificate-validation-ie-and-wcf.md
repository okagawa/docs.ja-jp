---
title: Internet Explorer と WCF で実行されるサービス証明書の検証の相違点
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 574a6fa5411bcb662514982923e5c51200f98ae2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272203"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Internet Explorer と WCF で実行されるサービス証明書の検証の相違点

HTTPS の使用時に Internet Explorer と Windows Communication Foundation (WCF) がサービス証明書を検証する方法が異なるため、WCF クライアントがサービスエンドポイントにメッセージを正常に送信できる場合でも、Internet Explorer がサービスのヘルプページまたは Web サービス記述言語 (WSDL) にアクセスできない可能性があります。 これは、Internet Explorer によって、サービス証明書の `ServerAuthentication` 拡張使用フラグにオブジェクト識別子 (OID) があるかどうかが確認されるのに対し、WCF ではこのような制約は適用されないためです。 サービスのサービスヘルプページまたは WSDL にアクセスできない場合は、 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) を使用してサービスメタデータにアクセスします。  
  
## <a name="see-also"></a>関連項目

- [HTTPS、SSL Over TCP、SOAP セキュリティ間における証明書検証方法の相違点](cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [方法: メタデータの取得および準拠サービスの実装をする](how-to-retrieve-metadata-and-implement-a-compliant-service.md)
