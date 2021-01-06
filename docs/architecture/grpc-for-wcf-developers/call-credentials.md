---
title: 資格情報の呼び出し-WCF 開発者向けの gRPC
description: ASP.NET Core 3.0 で gRPC 通話資格情報を実装して使用する方法。
ms.date: 12/15/2020
ms.openlocfilehash: 66394c75929bf068f83d631e022b467386e59ec5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938443"
---
# <a name="call-credentials"></a>資格情報を呼び出す

呼び出し資格情報は、すべての要求に対してメタデータで渡されたトークンに基づいています。

## <a name="ws-federation"></a>WS-Federation

ASP.NET Core は、 [Wsfederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet パッケージを使用した WS-Federation をサポートしています。 WS-Federation は、HTTP/2 でサポートされていない Windows 認証の代替手段として最も近いものです。 ユーザーは Active Directory フェデレーションサービス (AD FS) (AD FS) を使用して認証されます。これにより、ASP.NET Core での認証に使用できるトークンが提供されます。

この認証方法の使用を開始する方法の詳細については、「 [ASP.NET Core での WS-Federation を使用したユーザーの認証](/aspnet/core/security/authentication/ws-federation)」を参照してください。

## <a name="jwt-bearer-tokens"></a>JWT ベアラートークン

[JSON Web Token](https://jwt.io) (JWT) 標準は、エンコードされた文字列でユーザーとそのクレームに関する情報をエンコードする手段を提供します。 また、公開キー暗号化を使用して、コンシューマーがトークンの整合性を検証できるように、そのトークンに署名する方法も提供します。 IdentityServer4 などのさまざまなサービスを使用して、ユーザーを認証し、gRPC と HTTP Api で使用する OpenID Connect (OIDC) トークンを生成することができます。

ASP.NET Core 5.0 は JWT ベアラーパッケージを使用して JWTs を処理できます。 GRPC アプリケーションの構成は、ASP.NET Core MVC アプリケーションの場合とまったく同じです。 ここでは、JWT ベアラートークンに焦点を絞って説明します。これは、WS-FEDERATION を使用した開発が簡単であるためです。

## <a name="add-authentication-and-authorization-to-the-server"></a>サーバーに認証と承認を追加する

JWT ベアラーパッケージは、既定では ASP.NET Core 5.0 には含まれていません。 アプリに [AspNetCore JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet パッケージをインストールします。

スタートアップクラスに認証サービスを追加し、JWT ベアラーハンドラーを構成します。

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();

    var signingKey = ObtainSigningKeySomehow();

    services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
        .AddJwtBearer(options =>
        {
            options.TokenValidationParameters =
                new TokenValidationParameters
                {
                    ValidateAudience = false,
                    ValidateIssuer = false,
                    ValidateActor = false,
                    ValidateLifetime = true,
                    IssuerSigningKey = signingKey
                };
        });

}
```

プロパティは、 `IssuerSigningKey` 署名され `Microsoft.IdentityModels.Tokens.SecurityKey` たトークンを検証するために必要な暗号化データを使用して、の実装を必要とします。 このトークンは、Azure Key Vault などの *シークレットサーバー* に安全に格納します。

次に、承認サービスを追加します。これにより、システムへのアクセスが制御されます。

```csharp
    services.AddAuthorization(options =>
    {
        options.AddPolicy(JwtBearerDefaults.AuthenticationScheme, policy =>
        {
            policy.AddAuthenticationSchemes(JwtBearerDefaults.AuthenticationScheme);
            policy.RequireClaim(ClaimTypes.Name);
        });
    });

```

> [!TIP]
> 認証と承認は、2つの別個の手順です。 認証を使用して、ユーザーの id を決定します。 承認を使用して、ユーザーがシステムのさまざまな部分へのアクセスを許可されているかどうかを判断します。

次に、認証と承認のミドルウェアをメソッドの ASP.NET Core パイプラインに追加し `Configure` ます。

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    // Authenticate, then Authorize
    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

最後に、 `[Authorize]` セキュリティで保護されるすべてのサービスまたはメソッドに属性を適用し、 `User` 基になっているのプロパティを使用し `HttpContext` てアクセス許可を確認します。

```csharp
[Authorize]
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!TryValidateUser(request.TraderId, context.GetHttpContext().User))
    {
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Denied."));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}
```

## <a name="provide-call-credentials-in-the-client-application"></a>クライアントアプリケーションに呼び出し資格情報を提供する

Id サーバーから JWT トークンを取得したら、それを使用してクライアントからの gRPC 呼び出しを認証できます。その際、次のように呼び出しのメタデータヘッダーとして追加します。

```csharp
public async Task ShowPortfolioAsync(int portfolioId)
{
    var headers = new Grpc.Core.Metadata
    {
        { "Authorization", $"Bearer {_userToken}" }
    };
    var request = new GetRequest
    {
        TraderId = _userId,
        PortfolioId = portfolioId
    };
    var response = await _portfoliosClient.GetAsync(request, headers);

    // Display portfolio
}
```

これで、JWT ベアラートークンを呼び出し資格情報として使用して、gRPC サービスをセキュリティで保護しました。 [認証と承認を追加したポートフォリオサンプル gRPC アプリケーション](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth)のバージョンは、GitHub にあります。

>[!div class="step-by-step"]
>[前へ](security.md)
>[次へ](channel-credentials.md)
