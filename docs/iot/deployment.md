---
title: Raspberry Pi への .NET アプリのデプロイ
description: .NET アプリを Raspberry Pi にデプロイする方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: how-to
ms.prod: dotnet
ms.openlocfilehash: 4da558e2cdfc283d21f2a5497cb71dc746109614
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96594127"
---
# <a name="deploy-net-apps-to-raspberry-pi"></a>Raspberry Pi への .NET アプリのデプロイ

Raspberry Pi への .NET アプリのデプロイは、他のプラットフォームと同じです。 アプリは、 *自己完結* 型または *フレームワーク依存の* 配置モードとして実行できます。 各方法には利点があります。 詳細については、「 [.net アプリケーションの公開の概要](../core/deploying/index.md)」を参照してください。

## <a name="deploying-a-framework-dependent-app"></a>フレームワークに依存するアプリの配置

アプリをフレームワークに依存するアプリとしてデプロイするには、次の手順を実行します。

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. [Dotnet スクリプト](../core/tools/dotnet-install-script.md)を使用して、Raspberry Pi に .net をインストールします。 Raspberry Pi (ローカルまたは SSH) で Bash プロンプトから次の手順を実行します。
    1. 次のコマンドを実行して .NET をインストールします。

        ```bash
        curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin
        ```

        > [!NOTE]
        > これにより、最新バージョンがインストールされます。 特定のバージョンが必要な場合は、を `--version <VERSION>` 末尾に追加します。ここで、 `<VERSION>` は特定のビルドバージョンです。

    1. パスの解決を簡単にするには、 `DOTNET_ROOT` 次のコマンドを使用して、環境変数を追加し、 *dotnet* ディレクトリをに追加します。 `$PATH`

        ```bash
        echo 'export DOTNET_ROOT=$HOME/.dotnet' >> ~/.bashrc
        echo 'export PATH=$PATH:$HOME/.dotnet' >> ~/.bashrc
        source ~/.bashrc
        ```

    1. 次のコマンドを使用して、.NET インストールを確認します。

        ```dotnetcli
        dotnet --version
        ```

        表示されているバージョンが、インストールしたバージョンと一致していることを確認します。

1. 開発環境に応じて、次のようにして、開発用コンピューターにアプリを発行します。
    - **Visual Studio** を使用している場合は、[アプリケーションをローカルフォルダーに配置](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019)します。 発行する前に、発行プロファイルの概要で [ **編集** ] を選択し、[ **設定** ] タブを選択します。 **配置モード** が *フレームワークに依存* し、 **ターゲットランタイム** が *ポータブル* に設定されていることを確認します。
    - **.NET CLI** を使用している場合は、 [dotnet publish](../core/tools/dotnet-publish.md)コマンドを使用します。 追加の引数は必要ありません。

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. Raspberry Pi (ローカルまたは SSH) の Bash プロンプトから、アプリを実行します。 これを行うには、配置フォルダーを現在のディレクトリとして設定し、次のコマンドを実行します ( *HelloWorld.dll* はアプリのエントリポイントです)。

    ```dotnetcli
    dotnet HelloWorld.dll
    ```

## <a name="deploying-a-self-contained-app"></a>自己完結型アプリの展開

自己完結型アプリとしてアプリをデプロイするには、次の手順を実行します。

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. 開発環境に応じて、次のようにして、開発用コンピューターにアプリを発行します。
    - **Visual Studio** を使用している場合は、[アプリケーションをローカルフォルダーに配置](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019)します。 発行する前に、発行プロファイルの概要で [ **編集** ] を選択し、[ **設定** ] タブを選択します。 **配置モード** が " *自己完結型* " に設定されており、 **ターゲットランタイム** が " *linux-arm*" に設定されていることを確認します。
    - **.NET CLI** を使用している場合は、次の引数を指定して [dotnet publish](../core/tools/dotnet-publish.md)コマンドを使用し `-r linux-arm` ます。

        ```dotnetcli
        dotnet publish -r linux-arm
        ```

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. Raspberry Pi (ローカルまたは SSH) の Bash プロンプトから、アプリを実行します。 これを行うには、現在のディレクトリを配置場所に設定し、次の手順を実行します。
    1. 実行可能ファイルの *実行* アクセス許可を指定し `HelloWorld` ます (は実行可能ファイルの名前です)。

        ```bash
        chmod +x HelloWorld
        ```

    1. 実行可能ファイルを実行します。

        ```bash
        ./HelloWorld
        ```
