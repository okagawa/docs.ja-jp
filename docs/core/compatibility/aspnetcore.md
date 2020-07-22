---
title: ASP.NET Core の破壊的変更
titleSuffix: ''
description: ASP.NET Core における破壊的変更をリストアップします。
ms.date: 07/08/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: ca9e615e88964e1c37e9c0b721bca8c34bf671ac
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174394"
---
# <a name="aspnet-core-breaking-changes"></a>ASP.NET Core の破壊的変更

ASP.NET Core からは、.NET Core で使用される Web アプリ開発機能が提供されます。

このページでは、次の破壊的変更について説明します。

- [Antiforgery、CORS、Diagnostics、MVC、Routing の古い API の削除](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [認証:Google+ の非推奨](#authentication-google-deprecated-and-replaced)
- [認証:HttpContext.Authentication プロパティの削除](#authentication-httpcontextauthentication-property-removed)
- [認証:Newtonsoft.Json 型の置き換え](#authentication-newtonsoftjson-types-replaced)
- [認証:OAuthHandler ExchangeCodeAsync 署名の変更](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [承認:AddAuthorization のオーバーロードを別のアセンブリに移動](#authorization-addauthorization-overload-moved-to-different-assembly)
- [承認:AuthorizationFilterContext.Filters から IAllowAnonymous を削除](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [承認:IAuthorizationPolicyProvider の実装に新しいメソッドが必要](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [Azure:Microsoft というプレフィックスが付いた Azure 統合パッケージが削除された](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [Blazor:コンパイル時にコンポーネントからトリミングされる無意味な空白文字](#blazor-insignificant-whitespace-trimmed-from-components-at-compile-time)
- [キャッシュ:CompactOnMemoryPressure プロパティの削除](#caching-compactonmemorypressure-property-removed)
- [キャッシュ:Microsoft.Extensions.Caching.SqlServer で新しい SqlClient パッケージを使用](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [キャッシュ:ResponseCaching の "pubternal" 型を internal に変更](#caching-responsecaching-pubternal-types-changed-to-internal)
- [データ保護:DataProtection.AzureStorage で新しい Azure Storage API を使用](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [ 拡張機能:一部の NuGet パッケージに影響するパッケージ参照の変更](#extensions-package-reference-changes-affecting-some-nuget-packages)
- [ホスティング:Windows ホスティング バンドルから AspNetCoreModule V1 を削除](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [ホスティング:汎用ホストによる Startup コンストラクター挿入の制限](#hosting-generic-host-restricts-startup-constructor-injection)
- [ホスティング:IIS アウトプロセス アプリ用に HTTPS リダイレクトを有効化](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [ホスティング:IHostingEnvironment と IApplicationLifetime の型を置き換え](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [ホスティング:WebHostBuilder 依存関係から ObjectPoolProvider を削除](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [HTTP:Kestrel および IIS BadHttpRequestException の種類を古い形式としてマークし、置換](#http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced)
- [HTTP:ブラウザー SameSite の変更による認証への影響](#http-browser-samesite-changes-impact-authentication)
- [HTTP:DefaultHttpContext の機能拡張の削除](#http-defaulthttpcontext-extensibility-removed)
- [HTTP:HeaderNames フィールドを静的読み取り専用に変更](#http-headernames-constants-changed-to-static-readonly)
- [HTTP:IHttpClientFactory ログの整数状態コードによって作成された HttpClient インスタンス](#http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes)
- [HTTP:応答本文のインフラストラクチャの変更](#http-response-body-infrastructure-changes)
- [HTTP:一部の cookie SameSite の既定値の変更](#http-some-cookie-samesite-defaults-changed-to-none)
- [HTTP:同期 IO を既定で無効化](#http-synchronous-io-disabled-in-all-servers)
- [HttpSys:既定で無効になっているクライアント証明書の再ネゴシエーション](#httpsys-client-certificate-renegotiation-disabled-by-default)
- [ID:AddDefaultUI メソッド オーバーロードの削除](#identity-adddefaultui-method-overload-removed)
- [ID:UI ブートストラップ バージョンの変更](#identity-default-bootstrap-version-of-ui-changed)
- [ID:SignInAsync が認証されていない ID に対して例外をスロー](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [ID:SignInManager コンストラクターで新しいパラメーターの受け入れ](#identity-signinmanager-constructor-accepts-new-parameter)
- [ID:UI で静的な Web 資産機能を使用](#identity-ui-uses-static-web-assets-feature)
- [IIS:UrlRewrite ミドルウェア クエリ文字列は保持されます](#iis-urlrewrite-middleware-query-strings-are-preserved)
- [Kestrel:実行時に構成変更が既定で検出される](#kestrel-configuration-changes-at-run-time-detected-by-default)
- [Kestrel:接続アダプターを削除](#kestrel-connection-adapters-removed)
- [Kestrel:既定でサポートされている TLS プロトコル バージョンの変更](#kestrel-default-supported-tls-protocol-versions-changed)
- [Kestrel:空の HTTPS アセンブリを削除](#kestrel-empty-https-assembly-removed)
- [Kestrel:互換性のない Windows バージョンでの TLS 経由の HTTP/2 の無効化](#kestrel-http2-disabled-over-tls-on-incompatible-windows-versions)
- [Kestrel:要求トレーラー ヘッダーを新しいコレクションに移動](#kestrel-request-trailer-headers-moved-to-new-collection)
- [Kestrel:トランスポート抽象化レイヤーの変更](#kestrel-transport-abstractions-removed-and-made-public)
- [ローカリゼーション:API を古いとしてマーク](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [ローカリゼーション:"Pubternal" API の削除](#localization-pubternal-apis-removed)
- [ローカリゼーション:ResourceManagerWithCultureStringLocalizer クラスと WithCulture インターフェイス メンバーを削除](#localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed)
- [ログ:internal になった DebugLogger クラス](#logging-debuglogger-class-made-internal)
- [MVC:コントローラー アクション Async サフィックスを削除](#mvc-async-suffix-trimmed-from-controller-action-names)
- [MVC:JsonResult を Microsoft.AspNetCore.Mvc.Core に移動](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [MVC:プリコンパイル ツールを非推奨](#mvc-precompilation-tool-deprecated)
- [MVC:型を internal に変更](#mvc-pubternal-types-changed-to-internal)
- [MVC:Web API 互換性 shim を削除](#mvc-web-api-compatibility-shim-removed)
- [Razor:実行時コンパイルをパッケージに移動](#razor-runtime-compilation-moved-to-a-package)
- [セッション状態:古い API を削除](#session-state-obsolete-apis-removed)
- [共有フレームワーク:Microsoft.AspNetCore.App からアセンブリの削除](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [共有フレームワーク:Microsoft.AspNetCore.All を削除](#shared-framework-removed-microsoftaspnetcoreall)
- [SignalR:HandshakeProtocol.SuccessHandshakeData を置き換え](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [SignalR:HubConnection メソッドを削除](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [SignalR:HubConnectionContext コンストラクターを変更](#signalr-hubconnectioncontext-constructors-changed)
- [SignalR:JavaScript クライアント パッケージ名を変更](#signalr-javascript-client-package-name-changed)
- [SignalR:MessagePack ハブ プロトコルが MessagePack 2.x パッケージに移動された](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [SignalR:MessagePack ハブ プロトコル オプションの種類を変更](#signalr-messagepack-hub-protocol-options-type-changed)
- [SignalR:古い API](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [SignalR:UseSignalR メソッドと UseConnections メソッドが削除された](#signalr-usesignalr-and-useconnections-methods-removed)
- [SPA:SpaServices および NodeServices コンソール ロガー フォールバックの既定値を変更](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [SPA:SpaServices および NodeServices を古いとしてマーク](#spas-spaservices-and-nodeservices-marked-obsolete)
- [静的ファイル: CSV コンテンツ タイプが標準準拠に変更されました](#static-files-csv-content-type-changed-to-standards-compliant)
- [ターゲット フレームワーク: .NET Framework がサポートされない](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a>ASP.NET Core 5.0

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE[Blazor: Insignificant whitespace trimmed from components at compile time](~/includes/core-changes/aspnetcore/5.0/blazor-components-trim-insignificant-whitespace.md)]

***

[!INCLUDE[Extensions: Package reference changes](~/includes/core-changes/aspnetcore/5.0/extensions-package-reference-changes.md)]

***

[!INCLUDE[HTTP: HttpClient instances created by IHttpClientFactory log integer status codes](~/includes/core-changes/aspnetcore/5.0/http-httpclient-instances-log-integer-status-codes.md)]

***

[!INCLUDE[HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced](~/includes/core-changes/aspnetcore/5.0/http-badhttprequestexception-obsolete.md)]

***

[!INCLUDE[HttpSys: Client certificate renegotiation disabled by default](~/includes/core-changes/aspnetcore/5.0/httpsys-client-certificate-renegotiation-disabled-by-default.md)]

***

[!INCLUDE[IIS: UrlRewrite middleware query strings are preserved](~/includes/core-changes/aspnetcore/5.0/iis-urlrewrite-middleware-query-strings-are-preserved.md)]

***

[!INCLUDE[Kestrel: Configuration changes at run time detected by default](~/includes/core-changes/aspnetcore/5.0/kestrel-configuration-changes-at-run-time-detected-by-default.md)]

***
[!INCLUDE[Kestrel: Default supported TLS protocol versions changed](~/includes/core-changes/aspnetcore/5.0/kestrel-default-supported-tls-protocol-versions-changed.md)]

***

[!INCLUDE[Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions](~/includes/core-changes/aspnetcore/5.0/kestrel-disables-http2-over-tls.md)]

***

[!INCLUDE[Localization: "Pubternal" APIs removed](~/includes/core-changes/aspnetcore/5.0/localization-pubternal-apis-removed.md)]

***

[!INCLUDE[Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed](~/includes/core-changes/aspnetcore/5.0/localization-members-removed.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol options type changed](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-hub-protocol-options-changed.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

***

## <a name="aspnet-core-31"></a>ASP.NET Core 3.1

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a>ASP.NET Core 3.0

[!INCLUDE[Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed](~/includes/core-changes/aspnetcore/3.0/obsolete-apis-removed.md)]

***

[!INCLUDE[Authentication: Google+ deprecation](~/includes/core-changes/aspnetcore/3.0/authn-google-plus-authn-changes.md)]

***

[!INCLUDE[Authentication: HttpContext.Authentication property removed](~/includes/core-changes/aspnetcore/3.0/authn-httpcontext-property-removed.md)]

***

[!INCLUDE[Authentication: Newtonsoft.Json types replaced](~/includes/core-changes/aspnetcore/3.0/authn-apis-json-types.md)]

***

[!INCLUDE[Authentication: OAuthHandler ExchangeCodeAsync signature changed](~/includes/core-changes/aspnetcore/3.0/authn-exchangecodeasync-signature-change.md)]

***

[!INCLUDE[Authorization: AddAuthorization overload assembly change](~/includes/core-changes/aspnetcore/3.0/authz-assembly-change.md)]

***

[!INCLUDE[Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters](~/includes/core-changes/aspnetcore/3.0/authz-iallowanonymous-removed-from-collection.md)]

***

[!INCLUDE[Authorization: IAuthorizationPolicyProvider implementations require new method](~/includes/core-changes/aspnetcore/3.0/authz-iauthzpolicyprovider-new-method.md)]

***

[!INCLUDE[Caching: CompactOnMemoryPressure property removed](~/includes/core-changes/aspnetcore/3.0/caching-memory-property-removed.md)]

***

[!INCLUDE[Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package](~/includes/core-changes/aspnetcore/3.0/caching-new-sqlclient-package.md)]

***

[!INCLUDE[Caching: ResponseCaching types changed to internal](~/includes/core-changes/aspnetcore/3.0/caching-response-pubternal-to-internal.md)]

***

[!INCLUDE[Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs](~/includes/core-changes/aspnetcore/3.0/dataprotection-azstorage-using-azstorage-apis.md)]

***

[!INCLUDE[Hosting: ANCM version 1 removed from hosting bundle](~/includes/core-changes/aspnetcore/3.0/hosting-ancmv1-hosting-bundle-removal.md)]

***

[!INCLUDE[Hosting: Generic host restriction on Startup constructor injection](~/includes/core-changes/aspnetcore/3.0/hosting-generic-host-startup-ctor-restriction.md)]

***

[!INCLUDE[Hosting: HTTPS redirection enabled for IIS OutOfProcess](~/includes/core-changes/aspnetcore/3.0/hosting-https-redirection-iis-outofprocess.md)]

***

[!INCLUDE[Hosting: IHostingEnvironment and IApplicationLifetime types replaced](~/includes/core-changes/aspnetcore/3.0/hosting-ihostingenv-iapplifetime-types-replaced.md)]

***

[!INCLUDE[Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies](~/includes/core-changes/aspnetcore/3.0/hosting-objectpoolprovider-webhostbuilder-dependencies.md)]

***

[!INCLUDE[HTTP: DefaultHttpContext extensibility removed](~/includes/core-changes/aspnetcore/3.0/http-defaulthttpcontext-extensibility-removed.md)]

***

[!INCLUDE[HTTP: HeaderNames fields changed to static readonly](~/includes/core-changes/aspnetcore/3.0/http-headernames-constants-staticreadonly.md)]

***

[!INCLUDE[HTTP: Response body infrastructure changes](~/includes/core-changes/aspnetcore/3.0/http-response-body-changes.md)]

***

[!INCLUDE[HTTP: Some cookie SameSite default values changed](~/includes/core-changes/aspnetcore/3.0/http-cookie-samesite-defaults-change.md)]

***

[!INCLUDE[HTTP: Synchronous IO disabled by default](~/includes/core-changes/aspnetcore/3.0/http-synchronous-io-disabled.md)]

***

[!INCLUDE[Identity: AddDefaultUI method overload removed](~/includes/core-changes/aspnetcore/3.0/identity-ui-adddefaultui-overload-removed.md)]

***

[!INCLUDE[Identity: UI Bootstrap version change](~/includes/core-changes/aspnetcore/3.0/identity-ui-bootstrap-version.md)]

***

[!INCLUDE[Identity: SignInAsync throws exception for unauthenticated identity](~/includes/core-changes/aspnetcore/3.0/identity-signinasync-throws-exception.md)]

***

[!INCLUDE[Identity: SignInManager constructor accepts new parameter](~/includes/core-changes/aspnetcore/3.0/identity-signinmanager-ctor-parameter.md)]

***

[!INCLUDE[Identity: UI uses static web assets feature](~/includes/core-changes/aspnetcore/3.0/identity-ui-static-web-assets.md)]

***

[!INCLUDE[Kestrel: Connection adapters removed](~/includes/core-changes/aspnetcore/3.0/kestrel-connection-adapters-removed.md)]

***

[!INCLUDE[Kestrel: Empty HTTPS assembly removed](~/includes/core-changes/aspnetcore/3.0/kestrel-empty-assembly-removed.md)]

***

[!INCLUDE[Kestrel: Request trailer headers moved to new collection](~/includes/core-changes/aspnetcore/3.0/kestrel-request-trailer-headers.md)]

***

[!INCLUDE[Kestrel: Transport abstraction layer changes](~/includes/core-changes/aspnetcore/3.0/kestrel-transport-abstractions.md)]

***

[!INCLUDE[Localization: APIs marked obsolete](~/includes/core-changes/aspnetcore/3.0/localization-apis-marked-obsolete.md)]

***

[!INCLUDE[Logging: DebugLogger class made internal](~/includes/core-changes/aspnetcore/3.0/logging-debuglogger-to-internal.md)]

***

[!INCLUDE[MVC: Controller action Async suffix removed](~/includes/core-changes/aspnetcore/3.0/mvc-action-async-suffix-trimmed.md)]

***

[!INCLUDE[MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core](~/includes/core-changes/aspnetcore/3.0/mvc-jsonresult-moved.md)]

***

[!INCLUDE[MVC: Precompilation tool deprecated](~/includes/core-changes/aspnetcore/3.0/mvc-precompilation-tool-deprecated.md)]

***

[!INCLUDE[MVC: Types changed to internal](~/includes/core-changes/aspnetcore/3.0/mvc-pubternal-to-internal.md)]

***

[!INCLUDE[MVC: Web API compatibility shim removed](~/includes/core-changes/aspnetcore/3.0/mvc-webapi-compat-shim-removed.md)]

***

[!INCLUDE[Razor: Runtime compilation moved to a package](~/includes/core-changes/aspnetcore/3.0/razor-runtime-compilation-package.md)]

***

[!INCLUDE[Session state: Obsolete APIs removed](~/includes/core-changes/aspnetcore/3.0/session-obsolete-apis-removed.md)]

***

[!INCLUDE[Shared framework: Assembly removal from Microsoft.AspNetCore.App](~/includes/core-changes/aspnetcore/3.0/sharedfx-app-shared-framework-assemblies.md)]

***

[!INCLUDE[Shared framework: Microsoft.AspNetCore.All removed](~/includes/core-changes/aspnetcore/3.0/sharedfx-all-framework-removed.md)]

***

[!INCLUDE[SignalR: HandshakeProtocol.SuccessHandshakeData replaced](~/includes/core-changes/aspnetcore/3.0/signalr-successhandshakedata-replaced.md)]

***

[!INCLUDE[SignalR: HubConnection methods removed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnection-methods-removed.md)]

***

[!INCLUDE[SignalR: HubConnectionContext constructors changed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnectioncontext-ctors.md)]

***

[!INCLUDE[SignalR: JavaScript client package name change](~/includes/core-changes/aspnetcore/3.0/signalr-js-client-package-name.md)]

***

[!INCLUDE[SignalR: Obsolete APIs](~/includes/core-changes/aspnetcore/3.0/signalr-obsolete-apis.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices marked obsolete](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-obsolete.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices console logger fallback default change](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-fallback.md)]

***

[!INCLUDE[Target framework: .NET Framework not supported](~/includes/core-changes/aspnetcore/3.0/targetfx-netfx-tfm-support.md)]

***
