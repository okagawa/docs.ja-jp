---
title: WCF サービスと ASP.NET
description: WCF サービスを ASP.NET とサイドバイサイドでホストし、ASP.NET 互換モードでホストする方法について説明します。
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: 1d7401f6a326bc50923123acf803e26ce8238415
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246416"
---
# <a name="wcf-services-and-aspnet"></a>WCF サービスと ASP.NET

このトピックでは、Windows Communication Foundation (WCF) サービスを ASP.NET とサイドバイサイドでホストし、ASP.NET 互換モードでホストする方法について説明します。

## <a name="hosting-wcf-side-by-side-with-aspnet"></a>WCF を ASP.NET とサイドバイサイドでホストする

インターネットインフォメーションサービス (IIS) でホストされる WCF サービスは、で見つけることができます。1つの共通アプリケーションドメイン内の ASPX ページと ASMX Web サービス。 ASP.NET は、AppDomain 管理や、ASP.NET HTTP ランタイムの動的コンパイルなどの一般的なインフラストラクチャサービスを提供します。 WCF の既定の構成は、ASP.NET とサイドバイサイドで構成されます。

![WCF サービスと ASP .NET の共有状態を示すスクリーンショット。](./media/wcf-services-and-aspnet/windows-communication-foundation-services-asp-dotnet-configuration.gif)

ASP.NET HTTP ランタイムは ASP.NET 要求を処理しますが、これらのサービスが ASP.NET コンテンツと同じ AppDomain でホストされている場合でも、WCF サービス宛ての要求の処理には参加しません。 Wcf サービスモデルでは、wcf サービス宛てのメッセージをインターセプトし、WCF トランスポート/チャネルスタックを介してルーティングします。

この結果、サイド バイ サイド モデルは次のようになります。

- ASP.NET と WCF サービスは AppDomain の状態を共有できます。 2つのフレームワークは同じ AppDomain に共存できるため、WCF は AppDomain の状態を ASP.NET (静的変数、イベントなど) と共有することもできます。

- WCF サービスは、ホスティング環境やトランスポートとは関係なく、一貫して動作します。 ASP.NET HTTP ランタイムは意図的に、IIS/ASP.NET ホスティング環境や HTTP 通信と強く結合する形で設計されています。 逆に、WCF は、ホスト環境間で一貫して動作するように設計されています (WCF は IIS の内部と外部の両方で一貫して動作します)。また、これらのエンドポイントの一部で HTTP 以外のプロトコルを使用している場合でも、IIS 7.0 以降でホストされるすべてのエンドポイントで一貫した動作

- AppDomain 内では、HTTP ランタイムによって実装される機能は ASP.NET コンテンツに適用されますが、WCF には適用されません。 ASP.NET アプリケーションプラットフォームの HTTP 固有の多くの機能は、ASP.NET コンテンツを含む AppDomain 内部でホストされる WCF サービスには適用されません。 このような機能の例を次に示します。

  - HttpContext: <xref:System.Web.HttpContext.Current%2A> `null` WCF サービス内からアクセスする場合は常にです。 代わりに、<xref:System.ServiceModel.Channels.RequestContext> を使用してください。

  - ファイルベースの承認: WCF セキュリティモデルでは、サービス要求が承認されているかどうかを判断するときに、サービスの .svc ファイルに適用されるアクセス制御リスト (ACL) を許可しません。

  - 構成ベースの URL 承認: 同様に、WCF セキュリティモデルは、System.web の構成要素で指定されている URL ベースの承認規則に準拠していません \<authorization> 。 サービスが ASP によってセキュリティ保護された URL 空間に存在する場合、WCF 要求ではこれらの設定は無視されます。NET の URL 承認規則。

  - HttpModule 機能拡張: WCF ホスティングインフラストラクチャは、イベントが発生したときに WCF 要求 <xref:System.Web.HttpApplication.PostAuthenticateRequest> をインターセプトし、ASP.NET HTTP パイプラインに処理を返しません。 パイプラインの後の段階で要求をインターセプトするようにコード化されたモジュールは、WCF 要求をインターセプトしません。

  - ASP.NET impersonation: 既定では、ASP.NET が System.web の構成オプションを使用して偽装を有効にするように設定されている場合でも、WCF 要求は常に IIS プロセス id として実行され \<identity impersonate="true" /> ます。

これらの制限は、IIS アプリケーションでホストされる WCF サービスにのみ適用されます。 ASP.NET コンテンツの動作は、WCF の存在による影響を受けません。

従来 HTTP パイプラインによって提供されていた機能を必要とする WCF アプリケーションでは、ホストとトランスポートに依存しない WCF の同等の使用を検討する必要があります。

- <xref:System.ServiceModel.OperationContext> (<xref:System.Web.HttpContext> の代わり)

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> (ASP.NET のファイル ベースまたは URL ベースの承認の代わり)

- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> または独自の階層チャネル (HTTP モジュールの代わり)

- System. Web 偽装ではなく WCF を使用して、各操作の偽装を行います。

または、WCF の ASP.NET 互換モードでサービスを実行することを検討してください。

## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>ASP.NET 互換モードでの WCF サービスのホスト

WCF モデルは、ホスティング環境やトランスポート間で一貫して動作するように設計されていますが、多くの場合、アプリケーションでこのような柔軟性が必要になることはありません。 WCF の ASP.NET 互換モードは、IIS の外部でホストする機能や、HTTP 以外のプロトコルを使用して通信することを必要としないが、ASP.NET Web アプリケーションプラットフォームのすべての機能を使用するシナリオに適しています。

Wcf ホスティングインフラストラクチャが WCF メッセージをインターセプトして HTTP パイプラインからルーティングする既定のサイドバイサイド構成とは異なり、ASP.NET 互換モードで実行されている WCF サービスは、ASP.NET HTTP 要求ライフサイクルに完全に参加します。 互換モードでは、WCF サービスは実装を介して HTTP パイプラインを使用し <xref:System.Web.IHttpHandler> ます。これは、ASPX ページおよび ASMX Web サービスの要求の処理方法と同様です。 その結果、WCF は、次の ASP.NET 機能に関して ASMX と同じように動作します。

- <xref:System.Web.HttpContext>: ASP.NET 互換モードで実行されている WCF サービスは <xref:System.Web.HttpContext.Current%2A> 、とそれに関連付けられた状態にアクセスできます。

- ファイルベースの承認: ASP.NET 互換モードで実行されている WCF サービスは、ファイルシステムのアクセス制御リスト (Acl) をサービスの .svc ファイルにアタッチすることによって、セキュリティで保護することができます。

- 構成可能な URL 承認: ASP。Wcf サービスが ASP.NET 互換モードで実行されている場合、WCF 要求に対しては、NET の URL 承認規則が適用されます。

- <xref:System.Web.HttpModuleCollection>拡張性: ASP.NET 互換モードで実行される WCF サービスは、ASP.NET HTTP 要求ライフサイクルに完全に参加するため、HTTP パイプラインで構成された HTTP モジュールは、サービス呼び出しの前後に WCF 要求を処理できます。

- ASP.NET Impersonation: WCF サービスは、ASP.NET 偽装スレッドの現在の id を使用して実行されます。これは、アプリケーションに対して ASP.NET Impersonation が有効になっている場合、IIS プロセス id とは異なる場合があります。 ASP.NET impersonation と WCF impersonation の両方が特定のサービス操作に対して有効になっている場合、サービス実装は最終的に WCF から取得した id を使用して実行されます。

WCF の ASP.NET 互換モードは、アプリケーションレベルで次の構成 (アプリケーションの Web.config ファイルにあります) によって有効になります。

```xml
<system.serviceModel>
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```

この値が `false` 指定されていない場合、既定値はになります。 の値は、 `false` アプリケーションで実行されているすべての WCF サービスが ASP.NET 互換モードで動作しないことを示します。

ASP.NET 互換モードは、WCF の既定とは基本的に異なる要求の処理セマンティクスを意味するため、個々のサービスの実装では、ASP.NET 互換モードが有効になっているアプリケーション内で実行するかどうかを制御できます。 各サービスは、ASP.NET 互換モードをサポートするかどうかを、<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> で示すことができます。 この属性の既定値は <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> です。

```csharp
[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
public class CalculatorService : ICalculatorSession
{//Implement calculator service methods.}
```

アプリケーション全体を互換モードにしたとき、個々のサービスのサポート レベルがどうなるかを表に示します。

|アプリケーション全体の互換モード設定|AspNetCompatibilityRequirementsMode <br /><br /> 設定|実際の動作|
|--------------------------------------------------|---------------------------------------------------------|---------------------|
|aspNetCompatibilityEnabled = " `true` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|サービスは正常に動作します。|
|aspNetCompatibilityEnabled = " `true` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|サービスは正常に動作します。|
|aspNetCompatibilityEnabled = " `true` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|サービスがメッセージを受信した時点でアクティベーション エラーが発生します。|
|aspNetCompatibilityEnabled = " `false` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|サービスがメッセージを受信した時点でアクティベーション エラーが発生します。|
|aspNetCompatibilityEnabled = " `false` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|サービスは正常に動作します。|
|aspNetCompatibilityEnabled = " `false` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|サービスは正常に動作します。|

> [!NOTE]
> IIS 7.0 および WAS では、WCF サービスは、HTTP 以外のプロトコルを介して通信を行うことができます。 ただし、ASP.NET 互換モードが有効になっているアプリケーションで実行されている WCF サービスでは、非 HTTP エンドポイントの公開は許可されていません。 最初のメッセージを受信した時点で、アクティベーション例外が発生します。

WCF サービスの ASP.NET 互換モードを有効にする方法の詳細については、「」 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> および[ASP.NET の互換性](../samples/aspnet-compatibility.md)のサンプルを参照してください。

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>
- [AppFabric のホスティング機能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
