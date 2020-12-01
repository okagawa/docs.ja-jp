---
ms.openlocfilehash: f6e4c3d5c5fd020562e48515554136e0f8b6785c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032498"
---
### <a name="data-protection-dataprotectionblobs-uses-new-azure-storage-apis"></a>データの保護: DataProtection.Blobs では新しい Azure Storage API が使用されます

`Azure.Extensions.AspNetCore.DataProtection.Blobs` は [Azure Storage ライブラリ](https://github.com/Azure/azure-storage-net)に依存します。 これらのライブラリで、アセンブリ、パッケージ、名前空間の名前が変更されました。 ASP.NET Core 3.0 以降、`Azure.Extensions.AspNetCore.DataProtection.Blobs` では `Azure.Storage.` というプレフィックスが付いた新しい API およびパッケージが使用されます。

Azure Storage API に関する質問については、<https://github.com/Azure/azure-storage-net> を使用してください。 この問題に関するディスカッションについては、[dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570) を参照してください。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="old-behavior"></a>以前の動作

パッケージでは `WindowsAzure.Storage` NuGet パッケージが参照されていました。
パッケージでは `Microsoft.Azure.Storage.Blob` NuGet パッケージが参照されています。

#### <a name="new-behavior"></a>新しい動作

パッケージでは `Azure.Storage.Blob` NuGet パッケージが参照されています。

#### <a name="reason-for-change"></a>変更理由

この変更により、`Azure.Extensions.AspNetCore.DataProtection.Blobs` は推奨される Azure Storage パッケージに移行できるようになります。

#### <a name="recommended-action"></a>推奨アクション

ASP.NET Core 3.0 で古い Azure Storage API をまだ使用する必要がある場合は、パッケージ [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) または [Microsoft.Azure.Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.Blob/) に対する直接的な依存関係を追加してください。 このパッケージは、新しい `Azure.Storage` API と共にインストールできます。

多くの場合、アップグレードで必要なのは、新しい名前空間を使用するように `using` ステートメントを変更することだけです。

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
- using Microsoft.Azure.Storage;
- using Microsoft.Azure.Storage.Blob;
+ using Azure.Storage;
+ using Azure.Storage.Blobs;
```

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

なし

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
