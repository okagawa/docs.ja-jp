---
title: '軽減策: TLS プロトコル'
description: .NET Framework 4.6 以降の TLS プロトコル変更による影響と軽減策について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: 492315d43043c83d17eab330e8d589d1cffe7ad2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273868"
---
# <a name="mitigation-tls-protocols"></a>軽減策:TLS プロトコル

.NET Framework 4.6 から、<xref:System.Net.ServicePointManager?displayProperty=nameWithType> および <xref:System.Net.Security.SslStream?displayProperty=nameWithType> クラスで Tls1.0、Tls1.1、または Tls 1.2 の 3 つのプロトコルのいずれかを使用できるようになりました。 SSL3.0 プロトコルと RC4 の暗号化はサポートされていません。  
  
## <a name="impact"></a>影響  

 この変更は、以下のものに影響を与えます。  
  
- SSL を使用して <xref:System.Net.Http.HttpClient>、<xref:System.Net.HttpWebRequest>、<xref:System.Net.FtpWebRequest>、<xref:System.Net.Mail.SmtpClient>、<xref:System.Net.Security.SslStream> のいずれかのタイプで HTTPS サーバーまたはソケット サーバーと対話するすべてのアプリ。  
  
- Tls1.0、Tls1.1、または Tls 1.2 をサポートするためにアップグレードできない、すべてのサーバー サイド アプリ。  
  
## <a name="mitigation"></a>軽減策  

 推奨される軽減策はサーバー側のアプリを Tls1.0、Tls1.1、または Tls 1.2 にアップグレードすることです。 これが現実的でない場合、またはクライアント アプリが破損している場合は、次の 2 つの方法のいずれかにより、<xref:System.AppContext> クラスを使用してこの機能を除外できます。  
  
- プログラム的に。次のようにコード スニペットを使用します。  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <xref:System.Net.ServicePointManager> オブジェクトの初期化が行われるのは 1 回だけなので、アプリケーションはこれらの互換性設定の定義を最初に行う必要があります。  
  
- app.config ファイルの [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) セクションに次の行を追加する:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 ただし、既定の動作を除外することは、アプリケーションの安全性を低下させるので推奨されません。  
  
## <a name="see-also"></a>関連項目

- [アプリケーションの互換性](application-compatibility.md)
