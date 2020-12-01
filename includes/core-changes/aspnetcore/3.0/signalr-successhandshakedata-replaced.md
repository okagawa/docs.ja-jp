---
ms.openlocfilehash: 05aec429e28ef74515ef6988d5b064e6d16b7c1b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032672"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>SignalR:HandshakeProtocol.SuccessHandshakeData が置き換えられました

[HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) フィールドが削除され、特定の `IHubProtocol` が指定された場合に適切なハンドシェイク応答を生成するヘルパー メソッドに置き換えられました。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="old-behavior"></a>以前の動作

`HandshakeProtocol.SuccessHandshakeData` は、`public static ReadOnlyMemory<byte>` フィールドでした。

#### <a name="new-behavior"></a>新しい動作

`HandshakeProtocol.SuccessHandshakeData` は、指定されたプロトコルに基づいて `ReadOnlyMemory<byte>` を返す `static` `GetSuccessfulHandshake(IHubProtocol protocol)` メソッドに置き換えられました。

#### <a name="reason-for-change"></a>変更理由

ハンドシェイク _応答_ に、選択したプロトコルによって変化する非定数の追加フィールドが加えられました。

#### <a name="recommended-action"></a>推奨アクション

なし。 この型は、ユーザー コードから使用するように設計されていません。 これは `public` であり、SignalR サーバーとクライアントの間で共有できます。 また、.NET で記述されたユーザーの SignalR クライアントによって使用されることもあります。 SignalR の **ユーザー** は、この変更による影響を受けません。

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=nameWithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
