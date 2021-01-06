---
title: 自己ホスト型 gRPC アプリケーション-WCF 開発者向け gRPC
description: ASP.NET Core gRPC アプリケーションを自己ホスト型サービスとして展開する。
ms.date: 12/15/2020
ms.openlocfilehash: a5e2316b8d76593f4eb53760d2609b5bbbc9d2c5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938534"
---
# <a name="self-hosted-grpc-applications"></a>自己ホスト型 gRPC アプリケーション

ASP.NET Core 5.0 アプリケーションは Windows Server の IIS でホストできますが、HTTP/2 機能の一部がサポートされていないため、現在、IIS で gRPC アプリケーションをホストすることはできません。 この機能は、Windows Server の今後の更新プログラムの目的です。

アプリケーションを Windows サービスとして実行できます。 または、.NET 5.0 ホスト拡張機能の新機能により、 [systemd](https://en.wikipedia.org/wiki/Systemd)によって制御される Linux サービスとして実行できます。

## <a name="run-your-app-as-a-windows-service"></a>Windows サービスとしてのアプリの実行

Windows サービスとして実行するように ASP.NET Core アプリケーションを構成する [には、NuGet からパッケージを](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) インストールします。 次に、 `UseWindowsService` のメソッドにの呼び出しを追加し `CreateHostBuilder` `Program.cs` ます。

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseWindowsService() // Enable running as a Windows service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> アプリケーションが Windows サービスとして実行されていない場合、 `UseWindowsService` メソッドは何も実行しません。

ここで、次のいずれかの方法を使用してアプリケーションを発行します。

* Visual Studio で、プロジェクトを右クリックし、ショートカットメニューの [ **発行** ] を選択します。
* .NET CLI から。

.NET アプリケーションを発行するときに、 *フレームワークに依存* する展開と *自己完結* 型の展開のどちらを作成するかを選択できます。 フレームワークに依存する展開では、.NET 共有ランタイムが実行されているホストにインストールされている必要があります。 自己完結型の展開は、.NET ランタイムとフレームワークの完全なコピーを使用して発行され、任意のホストで実行できます。 各方法の長所と短所を含む詳細については、 [.net アプリケーションのデプロイ](../../core/deploying/index.md) に関するドキュメントを参照してください。

.NET 5.0 ランタイムをホストにインストールする必要がないアプリケーションの自己完結型のビルドを発行するには、アプリケーションに含めるランタイムを指定します。 `-r`(または) フラグを使用し `--runtime` ます。

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

フレームワークに依存するビルドを発行するには、フラグを省略し `-r` ます。

```dotnetcli
dotnet publish -c Release -o ./publish
```

ディレクトリの完全な内容 `publish` をインストールフォルダーにコピーします。 次に、 [sc ツール](/windows/desktop/services/controlling-a-service-using-sc) を使用して、実行可能ファイルの Windows サービスを作成します。

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a>Windows イベントログにログを記録する

メソッドは、 `UseWindowsService` ログメッセージを Windows イベントログに書き込むログ [記録](/aspnet/core/fundamentals/logging/) プロバイダーを自動的に追加します。 このプロバイダーのログ記録を構成するに `EventLog` `Logging` は、のセクション `appsettings.json` または別の構成ソースにエントリを追加します。

イベントログで使用されるソース名を上書きするには、 `SourceName` これらの設定でプロパティを設定します。 名前を指定しない場合は、既定のアプリケーション名 (通常は実行可能アセンブリ名) が使用されます。

ログ記録の詳細については、この章の最後を参照してください。

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>Systemd を使用してアプリを Linux サービスとして実行する

Linux サービス (Linux 用語の *デーモン* ) として実行するように ASP.NET Core アプリケーションを構成するには、NuGet から [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) パッケージをインストールします。 次に、 `UseSystemd` のメソッドにの呼び出しを追加し `CreateHostBuilder` `Program.cs` ます。

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseSystemd() // Enable running as a Systemd service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> アプリケーションが Linux サービスとして実行されていない場合、 `UseSystemd` メソッドは何も実行しません。

次に、アプリケーションを発行します。 アプリケーションは、フレームワークに依存するか、関連する Linux ランタイムに自己完結します (たとえば、 `linux-x64` )。 次のいずれかの方法を使用して発行できます。

* Visual Studio で、プロジェクトを右クリックし、ショートカットメニューの [ **発行** ] を選択します。
* .NET CLI から、次のコマンドを使用します。

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
ディレクトリの完全な内容 `publish` を、Linux ホストのインストールフォルダーにコピーします。 サービスを登録するには、 *ユニットファイル* と呼ばれる特殊なファイルをディレクトリに追加する必要があり `/etc/systemd/system` ます。 このフォルダーにファイルを作成するには、ルートアクセス許可が必要です。 使用する識別子と拡張子をファイルに付け `systemd` `.service` ます。 たとえば、 `/etc/systemd/system/myapp.service`を使用します。

次の例に示すように、サービスファイルは INI 形式を使用します。

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

`Type=notify`プロパティは、 `systemd` アプリケーションが起動時およびシャットダウン時に通知することを示します。 この設定により、 `WantedBy=multi-user.target` Linux システムが "ランダウン 2" に達したときにサービスが開始されます。これは、グラフィカルでないマルチユーザーシェルがアクティブであることを意味します。

はサービスを認識する前に、 `systemd` 構成を再読み込みする必要があります。 を制御する `systemd` には、コマンドを使用し `systemctl` ます。 再読み込みが完了したら、サブコマンドを使用して、 `status` アプリケーションが正常に登録されたことを確認します。

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

サービスが正しく構成されている場合は、次の出力が表示されます。

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

`start`コマンドを使用してサービスを開始します。

```console
sudo systemctl start myapp.service
```

> [!TIP]
> `.service`拡張機能は、を使用している場合は省略可能です `systemctl start` 。

システムの起動時にサービスを自動的に開始するように指定するには、 `systemd` コマンドを使用し `enable` ます。

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Journald にログを記録する

Linux と同等の Windows イベントログは `journald` 、の一部である構造化されたログ記録システムサービスです `systemd` 。 Linux デーモンによって標準出力に書き込まれたログメッセージは、自動的にに書き込まれ `journald` ます。 ログ記録レベルを構成するには、 `Console` ログ構成のセクションを使用します。 `UseSystemd`Host builder メソッドは、journal に合わせてコンソールの出力形式を自動的に構成します。

`journald`は Linux ログの標準であるため、さまざまなツールが統合されています。 から外部ログシステムにログを簡単にルーティングでき `journald` ます。 ホストでローカルに作業している場合は、コマンドを使用して `journalctl` コマンドラインからのログを表示できます。

```console
sudo journalctl -u myapp
```

> [!TIP]
> ホストで使用できる GUI 環境がある場合は、 *QJournalctl* や *gnome ログ* など、Linux で使用できるグラフィカルなログビューアーがいくつかあります。

を使用してコマンドラインからジャーナルにクエリを実行する方法の詳細については `systemd` `journalctl` 、 [manpages](https://manpages.debian.org/buster/systemd/journalctl.1)を参照してください。

## <a name="https-certificates-for-self-hosted-applications"></a>自己ホスト型アプリケーションの HTTPS 証明書

運用環境で gRPC アプリケーションを実行している場合は、信頼された証明機関 (CA) からの TLS 証明書を使用する必要があります。 この CA は、パブリック CA である場合もあれば、組織の内部の ca である場合もあります。

Windows ホストでは、クラスを使用して、セキュリティで保護された [証明書ストア](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) から証明書を読み込むことができ <xref:System.Security.Cryptography.X509Certificates.X509Store> ます。 また、 `X509Store` 一部の Linux ホストでは、OpenSSL キーストアでクラスを使用することもできます。

また、いずれかの [X509Certificate2 コンストラクター](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A)を使用して証明書を作成することもできます。

* ファイル ( `.pfx` 強力なパスワードで保護されたファイルなど)
* [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)などのセキュリティで保護されたストレージサービスから取得したバイナリデータ

証明書を使用するように Kestrel を構成するには、構成とコードの2つの方法があります。

### <a name="set-https-certificates-by-using-configuration"></a>構成を使用して HTTPS 証明書を設定する

構成方法では、 `.pfx` Kestrel 構成セクションで証明書ファイルへのパスとパスワードを設定する必要があります。 で `appsettings.json` は、これは次のようになります。

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "cert.pfx",
        "Password": "DO NOT STORE PLAINTEXT PASSWORDS IN APPSETTINGS FILES"
      }
    }
  }
}
```

Azure Key Vault または Hashicorp Vault などのセキュリティで保護された構成ソースを使用して、パスワードを指定します。

> [!IMPORTANT]
> 暗号化されていないパスワードを構成ファイルに保存しないでください。

### <a name="set-https-certificates-in-code"></a>コードでの HTTPS 証明書の設定

コードで Kestrel の HTTPS を構成するには、クラスのでメソッドを使用し `ConfigureKestrel` `IWebHostBuilder` `Program` ます。

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
            webBuilder.ConfigureKestrel(kestrel =>
            {
                kestrel.ConfigureHttpsDefaults(https =>
                {
                    https.ServerCertificate = new X509Certificate2("mycert.pfx", "password");
                });
            });
        });
```

ここでも、ファイルのパスワードをに保存 `.pfx` し、セキュリティで保護された構成ソースから取得するようにしてください。

>[!div class="step-by-step"]
>[前へ](grpc-in-production.md)
>[次へ](docker.md)
