---
title: Visual Studio for Mac を使用して .NET コンソール アプリケーションを発行する
description: Visual Studio for Mac を使用して、.NET アプリケーションを実行するために必要なファイルのセットを作成する方法について学習します。
ms.date: 11/30/2020
ms.openlocfilehash: 88f143011b19ca8eda6610803c894e619d06a635
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599188"
---
# <a name="tutorial-publish-a-net-console-application-using-visual-studio-for-mac"></a>チュートリアル: Visual Studio for Mac を使用して .NET コンソール アプリケーションを発行する

このチュートリアルでは、他のユーザーが実行できるコンソール アプリを発行する方法について説明します。 発行では、アプリケーションを実行するために必要なファイルのセットを作成します。 ファイルを配置するには、それをターゲット マシンにコピーします。

## <a name="prerequisites"></a>必須コンポーネント

- このチュートリアルでは、「[Visual Studio for Mac を使用して .NET コンソール アプリケーションを作成する](with-visual-studio-mac.md)」で作成したコンソール アプリを使用します。

## <a name="publish-the-app"></a>アプリの発行

1. Visual Studio for Mac を起動します。

1. 「[Visual Studio for Mac を使用して .NET コンソール アプリケーションを作成する](with-visual-studio-mac.md)」で作成した HelloWorld プロジェクトを開きます。

1. Visual Studio がアプリケーションのリリース バージョンをビルドしていることを確認します。 必要に応じて、ツール バーのビルド構成の設定を **[デバッグ]** から **[リリース]** に変更します。

   :::image type="content" source="media/publishing-with-visual-studio-mac/toolbar-release.png" alt-text="リリース ビルドが選択された Visual Studio のツールバー":::

1. メイン メニューから、 **[ビルド]**  >  **[フォルダーに発行...]** の順に選択します。

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-context-menu.png" alt-text="Visual Studio の [発行] コンテキスト メニュー":::

1. **[フォルダーに発行]** ダイアログで、 **[発行]** を選択します。

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-to-folder-dialog.png" alt-text="Visual Studio の [フォルダーに発行] ":::

   publish フォルダーが開き、作成されたファイルが表示されます。

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-folder.png" alt-text="publish フォルダー":::

1. 歯車アイコンを選択し、コンテキスト メニューから **[Copy "publish" as Pathname]\("publish" をパス名としてコピー\)** を選択します。

   :::image type="content" source="media/publishing-with-visual-studio-mac/copy-path.png" alt-text="publish フォルダーへのパスをコピーする":::

## <a name="inspect-the-files"></a>ファイルを検査する

この発行プロセスでは、フレームワークに依存する配置が作成されます。これは、.NET ランタイムがインストールされているコンピューター上で発行されたアプリケーションが実行される配置の種類です。 ユーザーは、コマンド プロンプトから `dotnet HelloWorld.dll` コマンドを実行することで、発行されたアプリを実行できます。

上の図に示すように、発行された出力には次のファイルが含まれます。

* *HelloWorld.deps.json*

  このファイルは、アプリケーションのランタイム依存関係ファイルです。 アプリの実行に必要な .NET コンポーネントとライブラリ (アプリケーションが含まれる動的リンク ライブラリを含む) を定義します。 詳細については、「[ランタイム構成ファイル](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)」を参照してください。

* *HelloWorld.dll*

   これは、[フレームワークに依存する展開](../deploying/deploy-with-cli.md#framework-dependent-deployment)バージョンのアプリケーションです。 このダイナミック リンク ライブラリを実行するには、コマンド プロンプトで`dotnet HelloWorld.dll` を入力します。 このアプリの実行方法は、.NET ランタイムがインストールされている任意のプラットフォームで動作します。

* *HelloWorld.pdb* (配置は省略可能)

   これは、デバッグ シンボル ファイルです。 このファイルはアプリケーションと一緒に配置する必要はありませんが、発行されるバージョンのアプリケーションをデバッグする必要がある場合に保存しておく必要があります。

* *HelloWorld.runtimeconfig.json*

   これは、アプリケーションのランタイム構成ファイルです。 ビルドされたアプリケーションの実行対象となる .NET のバージョンを識別します。 構成オプションを追加することもできます。 詳細については、[.NET ランタイム構成設定](../run-time-config/index.md#runtimeconfigjson)に関する記事を参照してください。

## <a name="run-the-published-app"></a>発行済みアプリを実行する

1. ターミナルを開いて *publish* フォルダーに移動します。 これを行うには、「`cd`」と入力してから前にコピーしたパスを貼り付けます。 次に例を示します。

   ```console
   cd ~/Projects/HelloWorld/HelloWorld/bin/Release/net5.0/publish/
   ```

1. `dotnet` コマンドを使用して、アプリを実行します。

   1. 「`dotnet HelloWorld.dll`」と入力し、<kbd>enter</kbd> キーを押します。

   1. プロンプトに応答して名前を入力し、任意のキーを押して終了します。

## <a name="additional-resources"></a>その他の技術情報

- [.NET アプリケーションの配置](../deploying/index.md)

## <a name="next-steps"></a>次の手順

このチュートリアルでは、コンソール アプリを発行しました。 次のチュートリアルでは、クラス ライブラリを作成します。

> [!div class="nextstepaction"]
> [Visual Studio for Mac を使用して .NET ライブラリを作成する](library-with-visual-studio-mac.md)
