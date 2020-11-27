---
title: ワークフロー トレース
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: b5a8f650edfdade4a18999c5e7af38ca72112122
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273881"
---
# <a name="workflow-tracing"></a>ワークフロー トレース

ワークフロー トレースでは、.NET Framework のトレース リスナーを使用して診断情報を取得できます。 トレースは、アプリケーションで問題が検出された場合に有効にし、その問題が解決されたら、再度無効にすることが可能です。 ワークフローのデバッグ トレースを有効にする方法は 2 つあります。 また、イベント トレース ビューアーを使用してトレースを構成したり、<xref:System.Diagnostics> を使用してトレース イベントをファイルに送信したりすることができます。  
  
## <a name="enabling-debug-tracing-in-etw"></a>ETW でのデバッグ トレースの有効化  

 ETW を使用してトレースを有効化するには、次の手順に従ってイベント ビューアーでデバッグ チャネルを有効化します。  
  
1. イベント ビューアーで分析ログおよびデバッグ ログのノードに移動します。  
  
2. イベントビューアーのツリービューで、[ **イベントビューアー->アプリケーションとサービス >ログ]、[Microsoft >Windows->アプリケーションサーバー-アプリケーション**] の順に移動します。 [ **アプリケーションサーバー-アプリケーション** ] を右クリックし、[表示] を選択し **て、分析ログとデバッグログを表示 >** ます。 [ **デバッグ** ] を右クリックし、[ **ログを有効にする**] を選択します。  
  
3. ワークフローがデバッグを実行し、トレースが ETW デバッグ チャネルに出力されると、トレースをイベント ビューアーで参照できます。 **イベントビューアー->の [アプリケーションとサービスログ]->Microsoft->Windows->アプリケーションサーバー-アプリケーション**] に移動します。 [ **デバッグ** ] を右クリックし、[ **更新**] を選択します。  
  
4. 既定の分析トレースのバッファー サイズは 4 KB ですが、このサイズを 32 KB に増やすことをお勧めします。 このためには、次の手順を実行します。  
  
    1. 現在のフレームワークのディレクトリ (C:\Windows\Microsoft.NET\Framework\v4.0.21203 など) で、次のコマンドを実行します。`wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`  
  
    2. \<bufferSize>ApplicationServer ファイルの値を32に変更します。  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3. 現在のフレームワークのディレクトリ (C:\Windows\Microsoft.NET\Framework\v4.0.21203 など) で、次のコマンドを実行します。`wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`  
  
> [!NOTE]
> .NET Framework 4 クライアントプロファイルを使用している場合は、まず、.NET Framework 4 ディレクトリから次のコマンドを実行して、ETW マニフェストを登録する必要があります。 `ServiceModelReg.exe –i –c:etw`  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a>System.Diagnostics によるデバッグ トレースの有効化  

 これらのリスナーは、ワークフロー アプリケーションの App.config ファイルまたはワークフロー サービスの Web.config ファイルで構成します。 この例では、は、 <xref:System.Diagnostics.TextWriterTraceListener> トレース情報を現在のディレクトリの MyTraceLog.txt ファイルに保存するように構成されています。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.Activities" switchValue="Information">  
        <listeners>  
          <add name="textListener" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"  
           type="System.Diagnostics.TextWriterTraceListener"  
           initializeData="MyTraceLog.txt"  
           traceOutputOptions="ProcessId, DateTime" />  
    </sharedListeners>  
    <trace autoflush="true" indentsize="4">  
      <listeners>  
        <add name="textListener" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [Windows Server App Fabric の監視](/previous-versions/appfabric/ee677251(v=azure.10))
- [App Fabric を使用したアプリケーションの監視](/previous-versions/appfabric/ee677276(v=azure.10))
