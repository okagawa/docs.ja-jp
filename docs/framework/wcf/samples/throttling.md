---
title: Throttling
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, throttling sample
- Throttling Sample [Windows Communication Foundation]
ms.assetid: 40bb3582-8ae9-4410-96f0-6c515bfaf47c
ms.openlocfilehash: f007d153a04117df872ea2fcdc68af38c57b53b3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600868"
---
# <a name="throttling"></a>Throttling
調整のサンプルでは、調整コントロールの使用方法を示します。 調整コントロールは、同時呼び出し、同時インスタンス、または同時セッションの数を制限して、リソースの過剰消費を防ぎます。 調整の動作は、サービス構成ファイルの設定で指定されます。 このサンプルは、電卓サービスを実装する[はじめに](getting-started-sample.md)に基づいています。  
  
 この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。  
  
> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 サービス構成ファイルでは、 [\<serviceThrottling>](../../configure-apps/file-schema/wcf/servicethrottling.md) 次のサンプル構成に示すように、の調整コントロールを指定します。  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <serviceMetadata httpGetEnabled="True"/>  
      <!-- Specify throttling behavior -->  
    <serviceThrottling maxConcurrentCalls="2"  
                       maxConcurrentInstances="10"/>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 上記の構成では、サービスは同時呼び出しの最大数を 2 に、同時インスタンスの最大数を 10 に制限しています。  
  
 調整の例を示すため、サービス メソッド上でスリープ時間を次のように定義しています。  
  
```csharp
public double Add(double n1, double n2)  
{  
    System.Threading.Thread.Sleep(2000);  
    return n1 + n2;  
}  
```  
  
 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。 Add メソッドと Subtract メソッドは同時に実行され、Multiply メソッドと Divide メソッドは同時に実行されます。このようにして、同時実行できるメソッドは 2 つ以下であることが証明され、調整の例が示されます。  
  
```console  
Press <ENTER> to terminate client.  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Add Result: 115.99  
Subtract Result: 68.46  
Multiply Result: 731.25  
Divide Result: 3.14285714285714  
  
Press any key to continue . . .  
```  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Throttling`  
