---
ms.openlocfilehash: 3932cf51b5194dba7956cd62ced3985a2e6311f0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506803"
---

<!-- Note, this content is copied in ../macos.md. Any fixes should be applied there too, though content may be different -->

パッケージ マネージャーの代わりに、SDK とランタイムをダウンロードして手動でインストールすることもできます。 手動インストールは、通常、継続的インテグレーション テストの一環として、またはサポートされていない Linux ディストリビューションで実行されます。 開発者またはユーザーにとっては、通常はパッケージ マネージャーを使用することをお勧めします。

.NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。 まず、次のいずれかのサイトから SDK またはランタイムの **バイナリ** リリースをダウンロードします。

- ✔️ [.NET 5.0 のダウンロード](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [.NET Core 3.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ✔️ [.NET Core 2.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [すべての .NET Core のダウンロード](https://dotnet.microsoft.com/download/dotnet-core)

次に、ダウンロードしたファイルを抽出し、`export` コマンドを使用して .NET で使用される変数を設定してから、.NET が PATH に含まれていることを確認します。

ランタイムを抽出し、.NET CLI コマンドをターミナルで使用できるようにするには、最初に .NET のバイナリ リリースをダウンロードします。 次に、ターミナルを開き、ファイルが保存されているディレクトリから次のコマンドを実行します。 アーカイブ ファイル名は、ダウンロードした内容によって異なる場合があります。

**次のコマンドを使用して、ランタイムを抽出します**。

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-5.0.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

**次のコマンドを使用して、SDK を抽出します**。

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-5.0.100-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> 上記の `export` コマンドでは、それを実行したターミナル セッションでのみ .NET CLI コマンドを使用できるようになります。
>
> シェル プロファイルを編集して、コマンドを永続的に追加することができます。 Linux ではさまざまなシェルを使用でき、それぞれに異なるプロファイルがあります。 次に例を示します。
>
> - **Bash シェル**: *~/.bash_profile*、 *~/.bashrc*
> - **Korn シェル**: *~/.kshrc* または *.profile*
> - **Z シェル**: *~/.zshrc* または *.zprofile*
>
> シェルの適切なソース ファイルを編集し、既存の `PATH` ステートメントの末尾に `:$HOME/dotnet` を追加します。 `PATH` ステートメントが含まれていない場合は、`export PATH=$PATH:$HOME/dotnet` を含む新しい行を追加します。
>
> また、ファイルの末尾に `export DOTNET_ROOT=$HOME/dotnet` を追加します。

この方法では、別々の場所に異なるバージョンをインストールして、どのアプリケーションにどれを使用するかを明示的に選択できます。
