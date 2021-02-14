---
ms.openlocfilehash: 3275865cf7f4669ba7deaacea320136d02f64dda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804236"
---

"**パッケージ {dotnet-package} が見つかりません**" や "**一部のパッケージをインストールできませんでした**" のようなエラー メッセージが表示される場合は、次のコマンドを実行します。

次の一連のコマンドには、2 つのプレースホルダーがあります。

- `{dotnet-package}`\
これは、`aspnetcore-runtime-3.1` など、インストールする .NET パッケージを表します。 これは、次の `sudo apt-get install` コマンドで使用されます。

- `{os-version}`\
これは、使用しているディストリビューションのバージョンを表します。 これは、次の `wget` コマンドで使用されます。 ディストリビューションのバージョンは、Ubuntu での `20.04` や Debian での `10` などの数値です。

まず、パッケージ リストを消去してみてください。

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

次に、.NET を再度インストールしてください。 それでも解決しない場合は、次のコマンドを使用して手動インストールを実行できます。
