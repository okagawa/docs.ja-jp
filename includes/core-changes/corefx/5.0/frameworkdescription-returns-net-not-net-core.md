---
ms.openlocfilehash: 80d13609f1b02ae0ac875b2028e745670bb8f503
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050568"
---
### <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a>FrameworkDescription の値が .NET Core ではなく .NET になる

<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> によって、".NET Core" ではなく ".NET" が返されるようになりました。

#### <a name="change-description"></a>変更内容

以前のバージョンの .NET では、<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> によって、説明文字列の一部として ".NET Core" が返されます。たとえば、`.NET Core 3.1.1` です。

.NET 5.0 以降は、<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> によって、説明文字列の一部として ".NET" が返されます。たとえば、`.NET 5.0.0` です。

#### <a name="reason-for-change"></a>変更理由

.NET 5 では、`netcoreapp` は、短いターゲット フレームワーク モニカーとして `net` に置き換えられます。 一貫性を確保するために、フレームワークの説明も更新されています。 `FrameworkName` は <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> プロパティ以外の場所ではエンコードされないため、変更は表面的なものになります。

#### <a name="version-introduced"></a>導入されたバージョン

5.0

#### <a name="recommended-action"></a>推奨アクション

<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> によって返される文字列で ".NET Core" を検索するすべてのコードを更新します。

#### <a name="category"></a>カテゴリ

Core .NET ライブラリ

#### <a name="affected-apis"></a>影響を受ける API

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
