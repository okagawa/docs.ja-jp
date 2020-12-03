---
title: NETSDK1071:'{0}' に対する PackageReference に指定された `{1}` のバージョン。
description: バージョン付きのフレームワークに含まれているメタパッケージに対する PackageReference の問題を解決する方法。
author: Forgind
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1071
ms.openlocfilehash: 1381fc63941ec04efb31035d13913620a195c236
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713081"
---
# <a name="netsdk1071-explicitly-versioned-packagereference-to-a-metapackage-that-would-be-included-with-the-framework"></a>NETSDK1071:フレームワークに含まれるメタパッケージに対する明示的にバージョン管理された PackageReference。

**この記事の対象:**  ✔️ .NET 5.0.100 SDK 以降のバージョン

.NET SDK から警告 NETSDK1071 を発行される場合、PackageReference に指定されているメタパッケージのバージョンと、TargetFramework プロパティを介して暗黙的に参照されているメタパッケージのバージョンとの間に、将来的にバージョンの競合が発生する可能性があることを示しています。

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

TargetFramework によってメタパッケージのバージョンが自動的に取り込まれるため、バージョンが異なる場合は競合します。

それを解決するには、次のようにします。

1. .NET Core または .NET Standard をターゲットとする場合は、プロジェクト ファイル内の `Microsoft.NETCore.App` または `NETStandard.Library` に対する明示的な参照を回避することを検討します。
2. .NET Core をターゲットとするときに特定バージョンのランタイムが必要な場合は、メタパッケージを直接参照するのではなく、`<RuntimeFrameworkVersion>` プロパティを使用します。 たとえば、これは、[自己完結型の展開](../../deploying/index.md#publish-self-contained)を使用していて、1.0.0 LTS ランタイムの特定のパッチが必要な場合に発生する可能性があります。
3. .NET Standard を対象にするときに特定バージョンの `NetStandard.Library` が必要な場合は、`<NetStandardImplicitPackageVersion>` プロパティを使用し、必要なバージョンに設定することができます。
4. .NET Framework プロジェクトで `Microsoft.NETCore.App` または `NETSTandard.Library` に対する参照を明示的に追加したり、更新したりしないでください。 NuGet により、.NET Standard ベースの NuGet パッケージを使用するときに必要な `NETStandard.Library` のバージョンが自動的にインストールされます。
5. .NET Core 2.1 以降を使用する場合は、.NET Core SDK によって適切なバージョンが自動的に選択されるため、`Microsoft.AspNetCore.App` または `Microsoft.AspNetCore.All` のバージョンを指定しないでください。 (メモ: これは、プロジェクトに `Microsoft.NET.Sdk.Web` も使用されている場合に、.NET Core 2.1 をターゲットとする場合にのみ機能します この問題は、.NET Core 2.2 SDK で解決されました)。
6. 警告が表示されないように、無効にすることもできます。

   ```xml
   <PackageReference Include="Microsoft.NetCore.App" Version="2.2.8" >
     <AllowExplicitVersion>true</AllowExplicitVersion>
   </PackageReference>
   ```
