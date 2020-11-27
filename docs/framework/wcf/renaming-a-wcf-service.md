---
title: WCF サービス名の変更
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 25f9201253f02f368ccf95ddf1f7a7d78d2e1b2f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249723"
---
# <a name="renaming-a-wcf-service"></a>WCF サービス名の変更

このトピックでは、Windows Communication Foundation (WCF) サービスの名前を変更する方法について説明します。  
  
## <a name="renaming-a-wcf-service"></a>WCF サービス名の変更  

 Windows Communication Foundation (WCF) テンプレートでサービスの名前を変更するには、次の手順を実行します。  
  
- サービスを実装するクラスの名前を変更します。  
  
- 次の例に示すように、このサービスの構成ファイルで、サービスの名前を新しい名前に変更します。 構成ファイルは、ホスト モデルに応じて、app.config または web.config ファイルのどちらかです。  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- サービスが web でホストされている場合は、 *\* .svc* ファイルを使用します。 この svc ファイルを開き、次の例に示すように、サービスの名前を変更します。 自己ホスト アプリケーションには svc ファイルがないので、この手順は必要ありません。  
  
```aspx-csharp
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a>WCF サービス コントラクト名の変更  
  
- サービス コントラクトの名前を変更するには、次の手順を実行します。  
  
- サービス コントラクトの名前を変更します。  
  
- 次の例に示すように、このサービスの構成ファイルで、サービス コントラクトの名前を新しい名前に変更します。 構成ファイルは、ホスト モデルに応じて、app.config または web.config ファイルのどちらかです。  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
