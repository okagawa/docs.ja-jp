---
title: ネットワークに関する破壊的変更
description: .NET Core のネットワークに関する破壊的変更の一覧を示します。
ms.date: 05/05/2020
ms.openlocfilehash: fdbd3f3bdcae5048b4f01e4d827f8a0e876c5c15
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050522"
---
# <a name="networking-breaking-changes"></a>ネットワークに関する破壊的変更

このページでは、次の破壊的変更について説明します。

| 互換性に影響する変更点 | 導入されたバージョン |
| - | - |
| [NegotiateStream と SslStream によって連続した Begin 操作を許可する](#negotiatestream-and-sslstream-allow-successive-begin-operations) | 5.0 |
| [Socket.LocalEndPoint が SendToAsync を呼び出した後に更新される](#socketlocalendpoint-is-updated-after-calling-sendtoasync) | 5.0 |
| [.NET ランタイムからの WinHttpHandler の削除](#winhttphandler-removed-from-net-runtime) | 5.0 |
| [MulticastOption.Group で null 値を受け付けない](#multicastoptiongroup-doesnt-accept-a-null-value) | 5.0 |
| [現在、Cookie パスの処理は、RFC 6265 に準拠している](#cookie-path-handling-now-conforms-to-rfc-6265) | 5.0 |
| [HttpRequestMessage.Version の既定値が 1.1 に変更された](#default-value-of-httprequestmessageversion-changed-to-11) | 3.0 |
| [WebClient.CancelAsync がすぐにキャンセルされない場合がある](#webclientcancelasync-doesnt-always-cancel-immediately) | 2.0 |

## <a name="net-50"></a>.NET 5.0

[!INCLUDE [negotiatestream-sslstream-dont-fail-on-successive-begin-calls](../../../includes/core-changes/networking/5.0/negotiatestream-sslstream-dont-fail-on-successive-begin-calls.md)]

***

[!INCLUDE [localendpoint-updated-on-sendtoasync](../../../includes/core-changes/networking/5.0/localendpoint-updated-on-sendtoasync.md)]

***

[!INCLUDE [winhttphandler-removed-from-runtime](../../../includes/core-changes/networking/5.0/winhttphandler-removed-from-runtime.md)]

***

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

[!INCLUDE [cookie-path-conforms-to-rfc6265](../../../includes/core-changes/networking/5.0/cookie-path-conforms-to-rfc6265.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a>.NET Core 2.0

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
