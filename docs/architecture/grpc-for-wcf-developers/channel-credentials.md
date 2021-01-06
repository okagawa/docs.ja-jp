---
title: チャネル資格情報-WCF 開発者向け gRPC
description: ASP.NET Core 3.0 で gRPC チャネル資格情報を実装して使用する方法について説明します。
ms.date: 12/15/2020
ms.openlocfilehash: 3663bbf061156db957241e2a32dbb9c64562ade2
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938638"
---
# <a name="channel-credentials"></a>チャンネルの資格情報

名前が示すように、チャネルの資格情報は、基になる gRPC チャネルにアタッチされます。 標準形式のチャネル資格情報では、クライアント証明書認証が使用されます。 このプロセスでは、クライアントは接続を確立するときに TLS 証明書を提供し、サーバーは呼び出しを許可する前に、この証明書を検証します。

チャネル資格情報と呼び出し資格情報を組み合わせて、gRPC サービスに包括的なセキュリティを提供することができます。 チャネル資格情報は、クライアントアプリケーションがサービスへのアクセスを許可されていることを証明し、呼び出し資格情報は、クライアントアプリケーションを使用しているユーザーに関する情報を提供します。

クライアント証明書の認証は、ASP.NET Core と同じように、gRPC に対して機能します。 詳細については、「 [ASP.NET Core で証明書認証を構成する](/aspnet/core/security/authentication/certauth)」を参照してください。

開発目的では自己署名証明書を使用できますが、運用環境では、信頼された機関によって署名された適切な HTTPS 証明書を使用する必要があります。

## <a name="add-certificate-authentication-to-the-server"></a>サーバーに証明書認証を追加する

証明書認証は、ホストレベル (Kestrel サーバーなど) と ASP.NET Core パイプラインの両方で構成します。

### <a name="configure-certificate-validation-on-kestrel"></a>Kestrel で証明書の検証を構成する

クライアント証明書を要求するように Kestrel (ASP.NET Core HTTP サーバー) を構成し、必要に応じて、入力方向の接続を受け入れる前に、指定された証明書の検証を実行することができます。 この構成 `CreateWebHostBuilder` `Program` は、ではなく、クラスのメソッドで指定し `Startup` ます。

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            var serverCert = ObtainServerCertificate();
            webBuilder.UseStartup<Startup>()
                .ConfigureKestrel(kestrelServerOptions => {
                    kestrelServerOptions.ConfigureHttpsDefaults(opt =>
                    {
                        opt.ClientCertificateMode = ClientCertificateMode.RequireCertificate;

                        // Verify that client certificate was issued by same CA as server certificate
                        opt.ClientCertificateValidation = (certificate, chain, errors) =>
                            certificate.Issuer == serverCert.Issuer;
                    });
                });
        });

```

`ClientCertificateMode.RequireCertificate`この設定により、Kestrel はクライアント証明書を提供しない接続要求を直ちに拒否しますが、この設定自体によって提供される証明書は検証されません。 `ClientCertificateValidation`接続が確立された時点で、ASP.NET Core パイプラインが適用される前に、Kestrel がクライアント証明書を検証できるように、コールバックを追加します。 (この場合、コールバックは、サーバー証明書と同じ *証明機関* によって発行されたものであることを保証します。)

### <a name="add-aspnet-core-certificate-authentication"></a>ASP.NET Core 証明書認証の追加

証明書認証は、 [AspNetCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet パッケージによって提供されます。

メソッドに証明書認証サービスを追加 `ConfigureServices` し、メソッドで ASP.NET Core パイプラインに認証と承認を追加し `Configure` ます。

```csharp
public class Startup
{
    private readonly bool _isDevelopment;

    public Startup(IWebHostEnvironment env)
    {
        _isDevelopment = env.IsDevelopment();
    }

    public void ConfigureServices(IServiceCollection services)
    {
        services.AddAuthentication(CertificateAuthenticationDefaults.AuthenticationScheme)
            .AddCertificate(options =>
            {
                if (_isDevelopment)
                {
                    // DO NOT DO THIS IN PRODUCTION!
                    options.RevocationMode = X509RevocationMode.NoCheck;
                }
            });
        services.AddAuthorization();
        services.AddGrpc();
    }

    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        app.UseRouting();

        app.UseAuthentication();
        app.UseAuthorization();

        app.UseEndpoints(endpoints => { endpoints.MapGrpcService<GreeterService>(); });
    }
}
```

## <a name="provide-channel-credentials-in-the-client-application"></a>クライアントアプリケーションでチャネル資格情報を指定する

パッケージを使用して、 `Grpc.Net.Client` 接続に使用するに提供されるインスタンスで証明書を構成し <xref:System.Net.Http.HttpClient> `GrpcChannel` ます。

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        // Assume path to a client .pfx file and password are passed from command line
        // On Windows this would probably be a reference to the Certificate Store
        var cert = new X509Certificate2(args[0], args[1]);

        var handler = new HttpClientHandler();
        handler.ClientCertificates.Add(cert);
        var httpClient = new HttpClient(handler);

        var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
        {
            HttpClient = httpClient
        });

        var grpc = new Greeter.GreeterClient(channel);
        var response = await grpc.SayHelloAsync(new HelloRequest { Name = "Bob" });
        System.Console.WriteLine(response.Message);
    }
}
```

## <a name="combine-channelcredentials-and-callcredentials"></a>ChannelCredentials と CallCredentials を組み合わせる

証明書とトークン認証の両方を使用するようにサーバーを構成できます。 これを行うには、Kestrel サーバーに証明書の変更を適用し、ASP.NET Core で JWT ベアラーミドルウェアを使用します。

クライアントにとの両方を提供するには、メソッドを使用して `ChannelCredentials` `CallCredentials` `ChannelCredentials.Create` 呼び出し資格情報を適用します。 その場合でも、インスタンスを使用して証明書認証を適用する必要があり <xref:System.Net.Http.HttpClient> ます。 コンストラクターに任意の引数を渡すと `SslCredentials` 、内部クライアントコードが例外をスローします。 パッケージ `SslCredentials` `Grpc.Net.Client` `Create` との互換性を維持するために、パラメーターはパッケージのメソッドにのみ含まれてい `Grpc.Core` ます。

```csharp
var handler = new HttpClientHandler();
handler.ClientCertificates.Add(cert);

var httpClient = new HttpClient(handler);

var callCredentials = CallCredentials.FromInterceptor(((context, metadata) =>
    {
        metadata.Add("Authorization", $"Bearer {_token}");
    }));

var channelCredentials = ChannelCredentials.Create(new SslCredentials(), callCredentials);

var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
{
    HttpClient = httpClient,
    Credentials = channelCredentials
});

var grpc = new Portfolios.PortfoliosClient(channel);
```

> [!TIP]
> 証明書認証を使用しないクライアントには、メソッドを使用でき `ChannelCredentials.Create` ます。 これは、チャネルで行われるすべての呼び出しでトークン資格情報を渡すために便利な方法です。

[証明書認証が追加された Fullstockticker サンプル gRPC アプリケーション](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker)のバージョンは、GitHub にあります。

>[!div class="step-by-step"]
>[前へ](call-credentials.md)
>[次へ](encryption.md)
