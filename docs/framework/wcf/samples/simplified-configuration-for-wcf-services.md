---
title: WCF サービスの簡略化された構成
description: WCF を使用して、一般的なサービスとクライアントを実装して構成する方法について説明します。 サービスは、構成ファイルで指定されたエンドポイントを使用して通信します。
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 46a0c878b29de34219413a508799ddaddf507dd8
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246221"
---
# <a name="simplified-configuration-for-wcf-services"></a>WCF サービスの簡略化された構成
このサンプルでは、Windows Communication Foundation (WCF) を使用して、一般的なサービスとクライアントを実装して構成する方法を示します。 このサンプルは、他のすべての基本的な技術サンプルの基礎になります。  
  
 このサービスは、サービスと通信するためのエンドポイントを公開し、.NET Framework 4 の簡略化された構成を使用します。 .NET Framework 4 より前の場合、エンドポイントは通常、次の構成コード例に示すように、構成ファイル (Web.config) で定義されます。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 .NET Framework 4 では、 `<service>` 要素は省略可能です。 サービスでエンドポイントが定義されていない場合、各ベース アドレスのエンドポイントと実装されたコントラクトがサービスに追加されます。 このベース アドレスがコントラクト名に追加されてエンドポイントが決定され、バインドがアドレス スキームで決定されます。 次のコード例は、簡略化された構成ファイルを示しています。 構成されているように、 `http://localhost/servicemodelsamples/service.svc` 同じコンピューター上のクライアントからサービスにアクセスできます。 リモート コンピューター上のクライアントがサービスにアクセスするには、localhost の代わりに完全修飾ドメイン名を指定する必要があります。 既定では、サービスはメタデータを公開しません。 そのため、サービスは <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 動作を有効にします。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1. [Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。  
  
2. ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。  
  
3. 次の手順に従ってサンプルを実行します。  
  
    1. **サービス**プロジェクトを右クリックし、[**スタートアッププロジェクトに設定**] をクリックして、Ctrl キーを押し**ながら F5**キーを押します。  
  
    2. コンソール出力でサービスが動作していることが確認されるまで待機します。  
  
    3. **クライアント**プロジェクトを右クリックし、[**スタートアッププロジェクトに設定**] をクリックして、Ctrl キーを押し**ながら F5**キーを押します。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>関連項目

- [AppFabric の管理のサンプル](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))
- [簡略化された構成](../simplified-configuration.md)
