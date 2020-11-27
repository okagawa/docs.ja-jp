---
title: Visual Studio を使用して .NET コンソール アプリケーションを発行する
description: Visual Studio を使用して、.NET アプリケーションを実行するために必要なファイルのセットを作成する方法について学習します。
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: b0c6bd85ddf86f0eb11c56f01abb74a7e9786363
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916006"
---
# <a name="tutorial-publish-a-net-console-application-using-visual-studio"></a>チュートリアル: Visual Studio を使用して .NET コンソール アプリケーションを発行する

このチュートリアルでは、他のユーザーが実行できるコンソール アプリを発行する方法について説明します。 発行では、アプリケーションを実行するために必要なファイルのセットを作成します。 ファイルを配置するには、それをターゲット マシンにコピーします。

## <a name="prerequisites"></a>必須コンポーネント

- このチュートリアルでは、「[Visual Studio を使用して .NET コンソール アプリケーションを作成する](with-visual-studio.md)」で作成するコンソール アプリを使用します。

## <a name="publish-the-app"></a>アプリの発行

1. Visual Studio を起動します。

1. 「[Visual Studio を使用して .NET コンソール アプリケーションを作成する](with-visual-studio.md)」で作成した *HelloWorld* プロジェクトを開きます。

1. Visual Studio でリリース ビルド構成が使用されていることを確認します。 必要に応じて、ツール バーのビルド構成の設定を **[デバッグ]** から **[リリース]** に変更します。

   :::image type="content" source="media/publishing-with-visual-studio/visual-studio-toolbar-release.png" alt-text="リリース ビルドが選択された Visual Studio のツールバー":::

1. **HelloWorld** プロジェクト (HelloWorld ソリューションではなく) を右クリックし、メニューから **[発行]** を選びます。

   :::image type="content" source="media/publishing-with-visual-studio/publish-context-menu.png" alt-text="Visual Studio の [発行] コンテキスト メニュー":::

1. **[発行]** ページの **[ターゲット]** タブで、 **[フォルダー]** 、 **[次へ]** の順に選択します。

   :::image type="content" source="media/publishing-with-visual-studio/pick-publish-target.png" alt-text="Visual Studio で発行先を選択します":::

1. **[発行]** ページの **[特定のターゲット]** タブで、 **[フォルダー]** 、 **[次へ]** の順に選択します。

   :::image type="content" source="media/publishing-with-visual-studio/pick-specific-publish-target.png" alt-text="Visual Studio で特定の発行先を選択する":::

1. **[発行]** ページの **[場所]** タブで、 **[完了]** を選択します。

   :::image type="content" source="media/publishing-with-visual-studio/publish-page-loc-tab.png" alt-text="Visual Studio の [発行] ページの [場所] タブ":::

1. **[発行]** ウィンドウの **[発行]** タブで、 **[発行]** を選択します。

   :::image type="content" source="media/publishing-with-visual-studio/publish-page.png" alt-text="Visual Studio の [発行] ウィンドウ":::

## <a name="inspect-the-files"></a>ファイルを検査する

この発行プロセスでは、フレームワークに依存する展開が既定で作成されます。これは、.NET ランタイムがインストールされているコンピューター上で発行されたアプリケーションが実行される展開の種類です。 ユーザーは、実行可能ファイルをダブルクリックするか、コマンドプロンプトから `dotnet HelloWorld.dll` コマンドを実行することで、発行されたアプリを実行できます。

次の手順で、発行プロセスによって作成されるファイルを確認します。

1. **ソリューション エクスプローラー** で、 **[すべてのファイルを表示]** を選択します。

1. プロジェクト フォルダーで、*bin/Release/net5.0/publish* を展開します。

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="発行されたファイルを表示しているソリューション エクスプローラー":::

   この図に示すように、発行された出力には次のファイルが含まれます。

   * *HelloWorld.deps.json*

      このファイルは、アプリケーションのランタイム依存関係ファイルです。 アプリの実行に必要な .NET コンポーネントとライブラリ (アプリケーションが含まれる動的リンク ライブラリを含む) を定義します。 詳細については、「[ランタイム構成ファイル](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)」を参照してください。

   * *HelloWorld.dll*

      これは、[フレームワークに依存する展開](../deploying/deploy-with-cli.md#framework-dependent-deployment)バージョンのアプリケーションです。 このダイナミック リンク ライブラリを実行するには、コマンド プロンプトで`dotnet HelloWorld.dll` を入力します。 このアプリの実行方法は、.NET ランタイムがインストールされている任意のプラットフォームで動作します。

   * *HelloWorld.exe*

      これは、[フレームワークに依存する実行可能ファイル](../deploying/deploy-with-cli.md#framework-dependent-executable) バージョンのアプリケーションです。 これを実行するには、コマンド プロンプトで `HelloWorld.exe` を入力します。 ファイルはオペレーティング システム固有のものです。

   * *HelloWorld.pdb* (配置は省略可能)

      これは、デバッグ シンボル ファイルです。 このファイルはアプリケーションと一緒に配置する必要はありませんが、発行されるバージョンのアプリケーションをデバッグする必要がある場合に保存しておく必要があります。

   * *HelloWorld.runtimeconfig.json*

      これは、アプリケーションのランタイム構成ファイルです。 ビルドされたアプリケーションの実行対象となる .NET のバージョンを識別します。 構成オプションを追加することもできます。 詳細については、[.NET ランタイム構成設定](../run-time-config/index.md#runtimeconfigjson)に関する記事を参照してください。

## <a name="run-the-published-app"></a>発行済みアプリを実行する

1. **ソリューション エクスプローラー** で、 *[publish]* フォルダーを右クリックし、 **[完全なパスのコピー]** を選択します。

1. コマンド プロンプトを開いて、*publish* フォルダーに移動します。 これを行うには、「`cd`」と入力して、完全なパスを貼り付けます。 次に例を示します。

   ```console
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. 実行可能ファイルを使用してアプリを実行します。

   1. 「`HelloWorld.exe`」と入力して、<kbd>Enter</kbd> キーを押します。

   1. プロンプトに応答して名前を入力し、任意のキーを押して終了します。

1. `dotnet` コマンドを使用して、アプリを実行します。

   1. 「`dotnet HelloWorld.dll`」と入力して、<kbd>Enter</kbd> キーを押します。

   1. プロンプトに応答して名前を入力し、任意のキーを押して終了します。

## <a name="additional-resources"></a>その他の技術情報

- [.NET アプリケーションの配置](../deploying/index.md)

## <a name="next-steps"></a>次の手順

このチュートリアルでは、コンソール アプリを発行しました。 次のチュートリアルでは、クラス ライブラリを作成します。

> [!div class="nextstepaction"]
> [Visual Studio を使用して .NET クラス ライブラリを作成する](library-with-visual-studio.md)
