---
title: 自己ホスト
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: f5c46bc486e03cf86ada3a565a3c282cd81db286
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599946"
---
# <a name="self-host"></a>自己ホスト
このサンプルでは、自己ホスト型サービスをコンソール アプリケーションに実装する方法を示します。 このサンプルは、[はじめに](getting-started-sample.md)に基づいています。 サービス構成ファイルは、名前が Web.config から App.config に変更され、ホストが使用するベース アドレスを構成するように変更されました。 サービス ソース コードは、構成されたベース アドレスを提供するサービス ホストを作成して開く、静的な `Main` 関数を実装するように変更されました。 サービス実装は、操作ごとにコンソールに出力を書き込むように変更されました。 クライアントは、サービスのエンドポイント アドレスが正しく構成されたことを除き、変更されていません。  
  
> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルは、静的な main 関数を実装し、指定された <xref:System.ServiceModel.ServiceHost> 型の `CalculatorService` を作成します。次のサンプル コードを参照してください。  
  
```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost =
           new ServiceHost(typeof(CalculatorService)))  
    {  
        // Open the ServiceHost to create listeners
        // and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```  
  
 サービスがインターネット インフォメーション サービス (IIS) または Windows プロセス アクティブ化サービス (WAS) にホストされている場合、サービスのベース アドレスはホスト環境から提供されます。 自己ホスト型の場合は、ベース アドレスを手動で指定する必要があります。 これを行うには、 `add` [\<baseAddresses>](../../configure-apps/file-schema/wcf/baseaddresses.md) 次の [\<host>](../../configure-apps/file-schema/wcf/host.md) [\<service>](../../configure-apps/file-schema/wcf/service.md) サンプル構成で示すように、の子である子要素を使用します。  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
  ...  
</service>  
```  
  
 このサンプルを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。 どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. [Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。  
  
3. サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a>関連項目

- [AppFabric のホストおよび永続化のサンプル](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
