---
ms.openlocfilehash: 8de70b0c445aa48fc4c3249ccfc8c095890fb14c
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050524"
---
### <a name="socketlocalendpoint-is-updated-after-calling-sendtoasync"></a>Socket.LocalEndPoint が SendToAsync を呼び出した後に更新される

<xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> によって、<xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> プロパティの値がソケットのローカル アドレスに更新されます。

#### <a name="version-introduced"></a>導入されたバージョン

5.0 RC1

#### <a name="change-description"></a>変更内容

以前のバージョンの .NET では、<xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> によって、ソケット インスタンスの <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> プロパティの値が変更されることはありません。 .NET 5.0 以降では、<xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> が正常に完了した場合、<xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> の値は暗黙的にバインドされたソケットのローカル アドレスになります。 この新しい動作は、<xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> および <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)>/<xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)> の動作と同じです。

#### <a name="reason-for-change"></a>変更理由

この変更によって、[バグが修正](https://github.com/dotnet/runtime/issues/915)され、`SendTo` バリアントとの間で動作に一貫性を持たせます。

#### <a name="recommended-action"></a>推奨される操作

<xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> によって <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> の値が変更されないことを前提とするコードを変更します。

#### <a name="category"></a>カテゴリ

ネットワーキング

#### <a name="affected-apis"></a>影響を受ける API

- <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)`

-->
