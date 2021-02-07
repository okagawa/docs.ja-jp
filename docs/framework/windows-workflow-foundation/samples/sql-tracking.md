---
description: '詳細情報: SQL 追跡'
title: SQL 追跡
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 2b336839b9c63c0b7bde8b6451add00cb353fec6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741745"
---
# <a name="sql-tracking"></a>SQL 追跡

このサンプルでは、SQL データベースに追跡レコードを書き込むカスタム SQL 追跡参加要素を記述する方法を示します。 Windows Workflow Foundation (WF) は、ワークフローインスタンスの実行の可視性を得るためのワークフロー追跡機能を提供します。 追跡ランタイムでは、ワークフローの実行中にワークフロー追跡レコードが出力されます。 ワークフロー追跡の詳細については、「 [ワークフローの追跡とトレース](../workflow-tracking-and-tracing.md)」を参照してください。

## <a name="use-the-sample"></a>サンプルを使用する

1. SQL Server 2008、SQL Server 2008 Express、またはそれ以降のバージョンがインストールされていることを確認します。 サンプルと共にパッケージ化されているスクリプトは、SQL Express インスタンスをローカル コンピューターで使用していることが前提になります。 別のインスタンスがある場合は、データベース関連のスクリプトを変更してからサンプルを実行してください。

2. Scripts ディレクトリ (\WF\Basic\Tracking\SqlTracking\CS\Scripts) 内で Trackingsetup.cmd を実行して SQL Server 追跡データベースを作成します。 これによって、TrackingSample という名前のデータベースが作成されます。

   > [!NOTE]
   > このスクリプトでは、SQL Express の既定のインスタンスにデータベースが作成されます。 別のデータベース インスタンスにインストールする場合は、Trackingsetup.cmd スクリプトを編集してください。

3. Visual Studio 2010 で SqlTrackingSample .sln を開きます。

4. **Ctrl** + **Shift** + **B** キーを押して、ソリューションをビルドします。

5. **F5** キーを押してアプリケーションを実行します。

   ブラウザー ウィンドウが開き、アプリケーションのディレクトリの一覧が示されます。

6. ブラウザーで、StockPriceService.xamlx をクリックします。

7. ブラウザーに、[StockPriceService] ページが表示され、ローカル サービスの WSDL アドレスが示されます。 このアドレスをコピーします。

   ローカルサービスの WSDL アドレスの例は、 `http://localhost:65193/StockPriceService.xamlx?wsdl` です。

8. エクスプローラーを使用して、WCF テストクライアント (WcfTestClient.exe) を実行します。 これは、 *Microsoft Visual Studio 10.0 \ Common7\IDE ディレクトリ* にあります。

9. WCF テストクライアントで、[ **ファイル** ] メニューをクリックし、[ **サービスの追加**] を選択します。 テキスト ボックスにローカル サービスのアドレスを貼り付けます。 [**OK**] をクリックしてダイアログ ボックスを閉じます。

10. WCF テストクライアントで、[ **Getstockprice**] をダブルクリックします。 これにより、 `GetStockPrice` 1 つのパラメーターを受け取る操作が開き、値を入力 `Contoso` して、[ **呼び出し**] をクリックします。

11. 出力された追跡レコードが SQL データベースに書き込まれます。 追跡レコードを表示するには、SQL Management Studio で TrackingSample データベースを開き、テーブルに移動します。 テーブルで選択クエリを実行すると、それぞれのテーブルに格納されている追跡レコード内のデータが表示されます。

   SQL Server Management Studio の詳細については、「 [SQL Server Management Studio の概要](/sql/ssms/sql-server-management-studio-ssms)」を参照してください。 SQL Server Management Studio [こちら](https://aka.ms/ssmsfullsetup)からダウンロードしてください。

## <a name="uninstall-the-sample"></a>サンプルをアンインストールする

1. サンプル *ディレクトリ (-*----------/) で、スクリプトを実行します。

    > [!NOTE]
    > Trackingcleanup.cmd は、ローカル コンピューターの SQL Express 内にあるデータベースを削除しようとします。 別の SQL Server インスタンスを使用している場合は、Trackingcleanup.cmd を編集します。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。 このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a>関連項目

- [AppFabric の監視のサンプル](/previous-versions/appfabric/ff383407(v=azure.10))
