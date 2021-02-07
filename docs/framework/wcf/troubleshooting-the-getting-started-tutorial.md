---
description: 詳細については、Windows Communication Foundation チュートリアルの概要に関するページを参照してください。
title: Windows Communication Foundation チュートリアルの開始に関するトラブルシューティング
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: c57598da80beb7b95d324359f6f9cf7cab9a4879
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703394"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Windows Communication Foundation チュートリアルの開始に関するトラブルシューティング

この記事では、 [「チュートリアル: Windows Communication Foundation アプリケーションの概要](getting-started-tutorial.md)」の手順に従って発生する可能性のある最も一般的な問題とエラーの解決策について説明します。
  
## <a name="common-problems"></a>一般的な問題

**ハードドライブにプロジェクトファイルが見つかりません。**

 Visual Studio では、プロジェクトファイルは *C:\Users の \\ &lt; ユーザー名 &gt; \ ソース* に保存されます。  

***Svcutil.exe* によって生成された *App.config* ファイルが見つかりません。**

 Visual Studio では、[ **既存項目の追加** ] ウィンドウには、既定で次の拡張子を持つファイルのみが表示されます。

- *.cs*
- *.resx*
- *. 設定*
- *.xsd*
- *.wsdl*

すべてのファイルの種類を表示するには、[**既存項目の追加**] ウィンドウの右下隅にあるドロップダウンリストで [**すべてのファイル ( \* . \* )** ] を選択します。  
  
## <a name="common-errors"></a>一般的なエラー

### <a name="compile-the-service-application"></a>サービスアプリケーションをコンパイルする

**エラー BC30420 ' Sub Main ' が ' Getting ' に見つかりませんでした。**

Visual Basic アプリケーションのエントリポイントが正しくありません。 次のように変更します。

   1. [ **ソリューションエクスプローラー** ] ウィンドウで、[ **Getting] ホスト** フォルダーを選択し、ショートカットメニューの [ **プロパティ** ] をクリックします。
    a. [ **Gettingstartup ホスト** ] ウィンドウで、[ **スタートアップオブジェクト**] の一覧から [ **Service. プログラム** ] (または特定のアプリケーションのエントリポイント) を選択します。
    b. メインメニューから、[**ファイル**] [すべてを保存] を選択し  >  ます。

### <a name="run-the-service-application"></a>サービス アプリケーションの実行

**HTTP は URL ' http: \/ /+: 8000/GettingStarted/計算 Atorservice ' を登録できませんでした。プロセスにこの名前空間へのアクセス権がありません。**

 適切なアクセスを行うには、管理者特権で Windows Communication Foundation (WCF) サービスをホストするプロセスを開始します。

- Visual studio の場合: [**スタート**] メニューで visual studio プログラムを選択し、   >  ショートカットメニューの [**管理者として実行**] をクリックします。
- コンソールウィンドウの場合: [**スタート**] メニューの [**コマンドプロンプト**] を選択し、ショートカットメニューから [   >  **管理者として実行**] を選択します。
- エクスプローラーの場合: 実行可能ファイルを選択し、ショートカットメニューから [ **管理者として実行** ] を選択します。

### <a name="compile-the-client-application"></a>クライアントアプリケーションをコンパイルする

**' 電卓 Atorclient ' に ' ' の定義が含まれておらず、 \<method name> \<method name> 型 ' 電卓 atorclient ' の最初の引数を受け付ける拡張メソッド ' ' が見つかりませんでした。 using ディレクティブまたはアセンブリ参照が指定されていないことを確認してください。**  

属性でマークしたメソッドだけ `ServiceOperationAttribute` がパブリックに公開されます。 インターフェイスのメソッドから属性を省略すると `ServiceOperationAttribute` `ICalculator` 、コンパイル中にこのエラーメッセージが表示されます。  

**型または名前空間の名前 ' 電卓 Atorclient ' が見つかりませんでした。 using ディレクティブまたはアセンブリ参照が指定されていないことを確認してください。**

 *GeneratedProxy.cs* *(または生成された*) ファイルを *Svcutil.exe* ツールで生成したときに、クライアントプロジェクトに追加しないと、このエラーが発生します。  

### <a name="run-the-client-application"></a>クライアント アプリケーションを実行する

**ハンドルされない例外: EndpointNotFoundException: ' http:/ \/ localhost: 8000/GettingStarted/電卓 Atorservice ' に接続できませんでした。TCP エラーコード 10061: ターゲットコンピューターがアクティブに拒否したため、接続できませんでした。**

このエラーは、最初にサービスを開始せずにクライアントアプリケーションを実行した場合に発生します。 最初に、ホストアプリケーションを実行してサービスを開始し、クライアントアプリケーションを実行します。

### <a name="use-the-svcutilexe-tool"></a>Svcutil.exe ツールを使用する

**' Svcutil ' は、内部コマンド、外部コマンド、操作可能なプログラム、またはバッチファイルとして認識されません。**

 *Svcutil.exe* はシステムパスに存在する必要があります。 最も簡単な解決策は、Visual Studio コマンドプロンプトを使用することです。 **[スタート]** メニューから **[Visual Studio \<version>]** ディレクトリを選択し、 **[VS 用開発者コマンド プロンプト\<version>]** を選択します。 このコマンドプロンプトでは、Visual Studio の一部として出荷されたすべてのツールの正しい場所にシステムパスを設定します。  
  
### <a name="run-the-service-and-client-applications"></a>サービスとクライアントアプリケーションを実行する

**System.servicemodel.security.securitynegotiationexception: \/ ターゲット ' http:/ \/ localhost: 8000/gettingstarted/計算 atorservice ' の ' http:/localhost: 8000/GettingStarted/計算 atorservice ' による SOAP セキュリティネゴシエーションに失敗しました**  

このエラーは、ネットワークに接続されていないドメインに参加しているコンピューターで発生します。 コンピューターをネットワークに接続するか、サービスとクライアントの両方のセキュリティをオフにします。

セキュリティをオフにするには:

- サービスの場合は、を作成するコードを `WSHttpBinding` 次のコードに置き換えます。  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- クライアントの場合、構成ファイルで、要素の下の要素を次のように更新 **\<security>** **\<binding>** します。  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator">
      <security mode="None" />
    </binding
    ```  

## <a name="see-also"></a>関連項目  

 [WCF アプリケーションを使ってみる](getting-started-tutorial.md)  
 [WCF トラブルシューティングクイックスタート](wcf-troubleshooting-quickstart.md)  
 [セットアップに関する問題のトラブルシューティング](troubleshooting-setup-issues.md)
