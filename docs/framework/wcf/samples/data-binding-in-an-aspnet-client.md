---
title: ASP.NET クライアントでのデータ バインディング
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: 134e1d7df3ed6bb245a870ad257fa64ad94e4e9c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602597"
---
# <a name="data-binding-in-an-aspnet-client"></a>ASP.NET クライアントでのデータ バインディング
このサンプルでは、一般的な Windows Communication Foundation (WCF) サービスによって返されたデータを Web フォームアプリケーションにバインドする方法を示します。  
  
> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルでは、要求/応答通信パターンを定義するコントラクトを実装するサービスを示します。 このサンプルは、ブラウザーからアクセスできるクライアント Web フォームアプリケーションと、インターネットインフォメーションサービス (IIS) でホストされる WCF サービスで構成されています。  
  
 サービスは、要求/応答通信パターンを定義するコントラクトを実装します。 コントラクトは `IWeatherService` インターフェイスによって定義されます。このインターフェイスでは、`GetWeatherData` という名前の操作が公開されます。 この操作は都市名の配列を受け付け、各都市の予想最高気温と最低気温を表す `WeatherData` オブジェクトの配列を返します。  
  
 ASP.NET の .aspx ページでは、DataGrid Web コントロールが定義されています。これには、サービスによって返されるデータのグラフィック表示が含まれています。 .Aspx ページのコードは、気象データの WCF サービスを呼び出し、オブジェクトの配列にデータを返し `WeatherData` ます。 DataGrid の `DataSource` プロパティをこの配列に設定することにより、データを取得する場所を指定します。 データ バインディングは、DataGrid の `DataBind` メソッドが呼び出されたときに発生します。 このコードはすべて、内に含まれています。`aspx` ページの `Page_Load` メソッド。ユーザーがブラウザーページを更新するたびに、DataGrid のデータが更新されます。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. [Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。  
  
3. このサンプルのクライアントは、開発用 Web サーバーで実行される Web サイトです。 開発 Web サーバーを起動するには、コマンドプロンプトで「」と入力し `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client` ます。 次に、を参照し `http://localhost:8000/client` ます。 このサンプルを複数のコンピューターで実行するには、クライアントの Web.config ファイル内の `localhost` へのすべての参照をサーバーのコンピューター名に置き換えます。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
