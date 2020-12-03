---
title: '破壊的変更: 承認:エンドポイント ルーティングのリソースは HttpContext'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: 承認: エンドポイント ルーティングのリソースは HttpContext'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 7c5a77cb8999c60a7780b9b4f7ad2a1c79fd8310
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760010"
---
# <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a>承認:エンドポイント ルーティングのリソースは HttpContext

ASP.NET Core 3.1 でエンドポイント ルーティングを使用する場合、承認に使用されるリソースはエンドポイントです。 この方法は、ルート データ (<xref:Microsoft.AspNetCore.Routing.RouteData>) へのアクセスを付与するためには不十分でした。 MVC では以前、エンドポイント (<xref:Microsoft.AspNetCore.Http.Endpoint>) とルート データの両方にアクセスできるようにするため、<xref:Microsoft.AspNetCore.Http.HttpContext> リソースが渡されました。 この変更により、承認に渡されるリソースは常に `HttpContext` になります。

## <a name="version-introduced"></a>導入されたバージョン

5.0 Preview 7

## <a name="old-behavior"></a>以前の動作

エンドポイント ルーティングと承認ミドルウェア (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) または [[Authorize]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) 属性を使用する場合、承認に渡されるリソースは一致するエンドポイントです。

## <a name="new-behavior"></a>新しい動作

`HttpContext` がエンドポイント ルーティングから承認に渡されます。

## <a name="reason-for-change"></a>変更理由

`HttpContext` からエンドポイントにアクセスできます。 一方で、エンドポイントからルート データなどにアクセスする方法はありませんでした。 エンドポイント以外のルーティングからの機能に不足がありました。

## <a name="recommended-action"></a>推奨アクション

アプリでエンドポイント リソースが使用される場合は、`HttpContext` で <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> を呼び出して、エンドポイントへのアクセスを継続します。

ASP.NET Core 5.0 Preview 8 以降では、<xref:System.AppContext.SetSwitch%2A> を使用して以前の動作に戻すことができます。 次に例を示します。

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

## <a name="affected-apis"></a>影響を受ける API

None

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
