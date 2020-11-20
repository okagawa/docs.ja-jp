---
ms.openlocfilehash: aba7b473af7685aa45f7e093a2f75311687593df
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506986"
---

"**パッケージ {dotnet-package} が見つかりません**" や "**一部のパッケージをインストールできませんでした**" のようなエラー メッセージが表示される場合は、次のコマンドを実行します。

次の一連のコマンドには、2 つのプレースホルダーがあります。

- `{dotnet-package}`\
これは、`aspnetcore-runtime-3.1` など、インストールする .NET パッケージを表します。 これは、次の `sudo apt-get install` コマンドで使用されます。

- `{os-version}`\
これは、使用している Linux のバージョンを表します。 これは、次の `wget` コマンドで使用されます。

まず、パッケージ リストを消去してみてください。

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

次に、.NET を再度インストールしてください。 それでも解決しない場合は、次のコマンドを使用して手動インストールを実行できます。
