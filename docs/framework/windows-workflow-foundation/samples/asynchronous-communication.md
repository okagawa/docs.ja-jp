---
title: 非同期通信
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: db5a8f415479967d7579357bd0c8058c7fb961c5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255846"
---
# <a name="asynchronous-communication"></a>非同期通信

このサンプルでは、2つの異なる Windows Workflow Foundation (WF) サービス間の通信が既定で非同期に実行される方法を示します。  
  
## <a name="demonstrates"></a>対象  

 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サービス間の非同期通信  
  
## <a name="discussion"></a>ディスカッション  

 このサンプルでは、.NET Framework が提供するメッセージング アクティビティを使用して、[!INCLUDE[wf1](../../../../includes/wf1-md.md)] アプリケーション間の非同期通信がどのように行われるのかを示します。  
  
 このサンプルは、次の 3 つのプロジェクトで構成されています。  
  
 CreditCheckService  
 このサービスは、特定の個人のクレジット スコアまたは取得する項目の値を受け取り、その個人にクレジットを与えるかどうかを判断します。  
  
 RentalApprovalService  
 このサービスは、特定のクレジットを必要としている個人から申請を受け取ります。 このサービスは `CreditCheckService` と非同期で通信して、クレジットの申請が有効かどうかを判断します。  
  
 クライアント  
 クライアントは `RentalApprovalService` と同期通信を行い、クレジットが承認されているかどうかを調べます。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. **AsynchronousCommunication** ソリューションを右クリックし、[**プロパティ**] を選択します。  
  
2. [ **共通プロパティ**] で、[ **スタートアッププロジェクト**] を選択し、[ **マルチスタートアッププロジェクト**] を選択します。  
  
3. **RentalApprovalService** をリスト内の最初の位置、次に **CreditCheckService**、 **Client** の順に移動します。 3つのプロジェクトすべてに **開始** アクションを設定します。  
  
4. [ **OK**] をクリックし、F5 キーを押してサンプルを実行します。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
