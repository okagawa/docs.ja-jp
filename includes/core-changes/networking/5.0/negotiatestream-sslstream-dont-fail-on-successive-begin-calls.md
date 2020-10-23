---
ms.openlocfilehash: 16994e9cd97b31a30c8c5ce49d2042ff79b3f60b
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050523"
---
### <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a>NegotiateStream と SslStream によって連続した Begin 操作を許可する

セキュリティ ストリームでのエラー ケースの処理は異なり、`BeginAuthenticateAsServer` または `BeginAuthenticateAsClient` に対する連続した呼び出しが失敗しなくなりました。

#### <a name="version-introduced"></a>導入されたバージョン

5.0 RC1

#### <a name="change-description"></a>変更内容

以前のバージョンの .NET では、最初に `EndAuthenticateAsServer` または `EndAuthenticateAsClient` を呼び出さずに、`BeginAuthenticateAsServer` または `BeginAuthenticateAsClient` を連続して呼び出すと、<xref:System.NotSupportedException> になります。 .NET 5.0 以降では、これらの API は <xref:System.Threading.Tasks.Task> ベースの実装によってサポートされるため、`BeginAuthenticateAsServer` または `BeginAuthenticateAsClient` を連続して呼び出しても <xref:System.NotSupportedException> にはなりません。

#### <a name="reason-for-change"></a>変更理由

内部実装を非同期プログラミング モデル (APM) から <xref:System.Threading.Tasks.Task> ベースに切り替えると、パフォーマンスが向上し、コードの複雑さが軽減されます。

#### <a name="recommended-action"></a>推奨アクション

開発者側では、何も行う必要はありません。

#### <a name="category"></a>カテゴリ

ネットワーキング

#### <a name="affected-apis"></a>影響を受ける API

- <xref:System.Net.Security.SslStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.SslStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsClient`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient`

-->
