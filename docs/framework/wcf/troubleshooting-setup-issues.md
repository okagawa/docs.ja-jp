---
description: '詳細情報: セットアップに関する問題のトラブルシューティング'
title: セットアップに関する問題のトラブルシューティング
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 8beb404040c15ade8f435772fe1b947eef766702
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703472"
---
# <a name="troubleshoot-setup-issues"></a>セットアップに関する問題のトラブルシューティング

この記事では、Windows Communication Foundation (WCF) セットアップの問題をトラブルシューティングする方法について説明します。  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>.NET Framework 3.0 の MSI 修復操作の実行では修復されない一部の Windows Communication Foundation レジストリ キー  

 次のいずれかのレジストリ キーを削除した場合  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0  
  
 **コントロールパネル** の [**プログラムの追加と削除**] アプレットから起動した .NET Framework 3.0 インストーラーを使用して修復を実行した場合、キーは再作成されません。 これらのキーを正しく再作成するには、.NET Framework 3.0 をアンインストール後、再インストールする必要があります。  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-wmi-provider"></a>Wmi サービスの破損によって WMI プロバイダーのインストールがブロックされる

 .NET Framework 3.0 パッケージをインストールすると、WMI サービスの破損によって Windows Communication Foundation WMI プロバイダーのインストールがブロックされる場合があります。 インストール中に、Windows Communication Foundation インストーラーは、 *mofcomp.exe* コンポーネントを使用して、WCF *.mof* ファイルを登録できません。 発生する現象を次に示します。  
  
1. .NET Framework 3.0 のインストールは正常に完了するのに、WCF WMI プロバイダーが登録されない。  
  
2. アプリケーション イベント ログに、WCF の WMI プロバイダーの登録、または mofcomp.exe の実行に関する問題を示すエラー イベントが表示される。  
  
3. ユーザーの %temp% ディレクトリの dd_wcf_retCA* という名前のセットアップ ログ ファイルに、WCF WMI プロバイダーの登録に失敗したことが示される。  
  
4. イベント ログまたはセットアップ トレース ログ ファイルに、次の例外のいずれかが記録される。  
  
     ServiceModelReg [11:09:59:046]: System.ApplicationException : "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof" で E:\WINDOWS\system32\wbem\mofcomp.exe を実行している間に予期しない結果 3 が発生しました  
  
     または  
  
     ServiceModelReg [07:19:33:843]: System.TypeInitializationException : 'System.Management.ManagementPath' の型初期化子が例外をスローしました。 ---> InteropServices (0x80040154 が): 次のエラーにより、CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} のコンポーネントの COM クラスファクトリを取得できませんでした: 80040154。  
  
     または  
  
     ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException : ファイルまたはアセンブリ 'C:\WINDOWS\system32\wbem\mofcomp.exe'、またはその依存関係の 1 つが読み込めませんでした。 指定されたファイルが見つかりません。  
  
     ファイル名 : C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 上で説明した問題を解決するためには、次の手順を実行する必要があります。  
  
1. WMI Diagnosis Utility を実行して、WMI サービスを修復します。 このツールの使用方法の詳細については、「 [WMI Diagnosis Utility](/previous-versions/tn-archive/ff404265(v%3dmsdn.10))」を参照してください。  
  
 **コントロールパネル** にある [**プログラムの追加と削除**] アプレットを使用して .NET Framework 3.0 インストールを修復するか、.NET Framework 3.0 をアンインストールまたは再インストールします。  
  
## <a name="repair-net-framework-30-after-net-framework-35-installation"></a>3.5 のインストール .NET Framework 後に .NET Framework 3.0 を修復する

 .NET Framework 3.5 をインストールした後に .NET Framework 3.0 の修復を実行すると、 *machine.config* で .NET Framework 3.5 によって導入された構成要素が削除されます。 ただし、 *web.config* ファイルはそのまま残ります。 この回避策としては、ARP を使用して .NET Framework 3.5 を修復するか、またはスイッチで [ワークフローサービス登録ツール (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) を使用し `/c` ます。  
  
 [ワークフローサービス登録ツール (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) については、microsoft.net \framework\v3.5\ または%windir%\Microsoft.NET\framework64\v3.5\ を参照してください。  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>.NET Framework 3.5 のインストール後に WCF/WF Webhost に対して IIS を適切に構成する  

 .NET Framework 3.5 インストールで WCF 関連の追加の IIS 構成設定の構成に失敗した場合、インストールログにエラーが記録されて続行されます。 WorkflowServices アプリケーションを実行しようとしても、必要な構成設定がないため、実行することはできません。 たとえば、xoml やルール サービスの読み込みに失敗する可能性があります。  
  
 この問題を回避するには、 [ワークフローサービス登録ツール (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) とスイッチを使用して、 `/c` コンピューター上で IIS スクリプトマップを適切に構成します。 [ワークフローサービス登録ツール (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) については、microsoft.net \framework\v3.5\ または%windir%\Microsoft.NET\framework64\v3.5\ を参照してください。  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule"></a>型 ' HttpModule ' を読み込めませんでした

**アセンブリ ' System.servicemodel, Version 3.0.0.0, Culture = ニュートラル, PublicKeyToken = b77a5c561934e089 ' から型 ' HttpModule ' を読み込めませんでした**

 このエラーは .NET Framework 4 がインストールされ、WCF HTTP アクティブ化が有効になっている場合に発生します。 この問題を解決するには、Visual Studio の開発者コマンドプロンプト内から次のコマンドを実行します。  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>関連項目

- [セットアップ手順](./samples/set-up-instructions.md)
