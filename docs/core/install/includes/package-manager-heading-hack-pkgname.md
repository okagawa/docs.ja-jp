---
ms.openlocfilehash: ab1006f706439bcf5129854da3d14538e5b690a2
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506864"
---

パッケージ マネージャーのフィードに追加されるパッケージは、変更可能な `{product}-{type}-{version}` の形式で名前が付けられます。

- **product**\
インストールする .NET 製品の種類。 有効なオプションは次のとおりです。

  - dotnet
  - aspnetcore

- **type**\
SDK またはランタイムを選択します。 有効なオプションは次のとおりです。

  - SDK
  - ランタイム

- **version**\
インストールする SDK またはランタイムのバージョン。 この記事では常に、サポートされている最新バージョンの手順について説明します。 有効なオプションは、次のようなリリース バージョンです。

  - 5.0
  - 3.1
  - 3.0
  - 2.1

  ダウンロードしようとしている SDK/ランタイムが Linux ディストリビューションで使用できない可能性があります。 サポートされているディストリビューションの一覧については、「[.NET Core の依存関係と要件](../linux.md)」を参照してください。

### <a name="examples"></a>使用例

- ASP.NET Core 5.0 ランタイムをインストールする: `aspnetcore-runtime-5.0`
- .NET Core 2.1 ランタイムをインストールする: `dotnet-runtime-2.1`
- .NET 5.0 SDK をインストールする: `dotnet-sdk-5.0`
- .NET Core 3.1 SDK をインストールする: `dotnet-sdk-3.1`

### <a name="package-missing"></a>パッケージがない

パッケージ バージョンの組み合わせが正しくない場合は、使用できません。 たとえば、ASP.NET Core SDK がない場合、SDK コンポーネントは .NET SDK に含まれています。 値 `aspnetcore-sdk-2.2` は正しくありません。`dotnet-sdk-2.2` にする必要があります .NET Core によってサポートされている Linux ディストリビューションの一覧については、[.NET の依存関係と要件](../linux.md)に関するページを参照してください。
