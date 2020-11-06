---
title: ネットワークの構成設定
description: .NET Core アプリのネットワークを構成するランタイム設定について説明します。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bda608e83bb1b093d7d9b860de9607f6734720aa
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188303"
---
# <a name="run-time-configuration-options-for-networking"></a>ネットワークのランタイム構成オプション

## <a name="http2-protocol"></a>HTTP/2 プロトコル

- HTTP/2 プロトコルのサポートを有効にするかどうかを構成します。

- .NET Core 3.0 で導入されました。

- .NET Core 3.0 のみ:この設定を省略した場合、HTTP/2 プロトコルのサポートは無効になります。 これは、値を `false` に設定した場合と同じです。

- .NET Core 3.1 および .NET 5+:この設定を省略した場合、HTTP/2 プロトコルのサポートは有効になります。 これは、値を `true` に設定した場合と同じです。

| | 設定の名前 | 値 |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false` - 無効<br/>`true` - 有効 |
| **環境変数** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0` - 無効<br/>`1` - 有効 |

## <a name="usesocketshttphandler"></a>UseSocketsHttpHandler

- <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> が <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> 以前の HTTP プロトコル スタック (Windows と `CurlHandler` では <xref:System.Net.Http.WinHttpHandler>、Linux では [libcurl](https://curl.haxx.se/libcurl/) の上位に実装された内部クラス) を使用するかどうかを構成します。

  > [!NOTE]
  > <xref:System.Net.Http.HttpClientHandler> クラスを直接インスタンス化するのではなく、高レベルのネットワーク API を使用している可能性があります。 この設定は、<xref:System.Net.Http.HttpClient> や [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)) などの高レベル ネットワーク API で使用される HTTP プロトコル スタックにも影響します。

- この設定を省略した場合、<xref:System.Net.Http.HttpClientHandler> では <xref:System.Net.Http.SocketsHttpHandler> が使用されます。 これは、値を `true` に設定した場合と同じです。

- この設定は、<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> メソッドを呼び出すことによりプログラムで構成できます。

| | 設定の名前 | 値 |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true` - <xref:System.Net.Http.SocketsHttpHandler> の使用を有効にする<br/>`false` - Windows では <xref:System.Net.Http.WinHttpHandler>、Linux では [libcurl](https://curl.haxx.se/libcurl/) の使用を有効にする |
| **環境変数** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1` - <xref:System.Net.Http.SocketsHttpHandler> の使用を有効にする<br/>`0` - Windows では <xref:System.Net.Http.WinHttpHandler>、Linux では [libcurl](https://curl.haxx.se/libcurl/) の使用を有効にする |

> [!NOTE]
> .NET 5 以降では、`System.Net.Http.UseSocketsHttpHandler` 設定は使用できなくなりました。

## <a name="latin1-headers-net-core-31-only"></a>Latin1 ヘッダー (.NET Core 3.1 のみ)

- このスイッチによって HTTP ヘッダー検証の緩和が許可され、<xref:System.Net.Http.SocketsHttpHandler> では、ISO-8859-1 (Latin-1) でエンコードされた文字をヘッダーで送信できます。

- この設定を省略した場合、ASCII 以外の文字を送信しようとすると <xref:System.Net.Http.HttpRequestException> が発生します。 これは、値を `false` に設定した場合と同じです。

| | 設定の名前 | 値 |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.SocketsHttpHandler.AllowLatin1Headers` | `false` - 無効<br/>`true` - 有効 |
| **環境変数** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_ALLOWLATIN1HEADERS` | `0` - 無効<br/>`1` - 有効 |

> [!NOTE]
> このオプションは .NET Core バージョン 3.1 9 以降の 3.1 でのみお使いになれます。それ以前またはそれ以降のバージョンでは利用できません。 .NET 5 では、<xref:System.Net.Http.SocketsHttpHandler.RequestHeaderEncodingSelector> の使用をお勧めします。
