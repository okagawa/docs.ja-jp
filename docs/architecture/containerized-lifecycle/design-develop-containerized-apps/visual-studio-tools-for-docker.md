---
title: Windows 上の Visual Studio Tools for Docker
description: Visual Studio 2017 バージョン 15.7 以降で使用できる Docker ツールについて説明します。
ms.date: 01/06/2021
ms.custom: vs-dotnet
ms.openlocfilehash: 0f6a0ca0e90021f5d374cfacc5c498f257ab5422
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970508"
---
# <a name="use-docker-tools-in-visual-studio-on-windows"></a>Windows 上の Visual Studio で Docker ツールを使用する

Visual Studio 2017 バージョン 15.7 以降に含まれている Docker ツールを使用する場合の開発者ワークフローは、Visual Studio Code と Docker CLI の使用と似ています (実際、同じ Docker CLI に基づいています) が、より簡単に始めることができ、プロセスが簡単であり、ビルド、実行、および構成タスクの生産性を高めることができます。 また、Visual Studio の通常の `F5` キーと `Ctrl+F5` キーを使用してコンテナーを実行およびデバッグすることもできます。 コンテナーがソリューション レベルで同じ `docker-compose.yml` ファイルに定義されている場合は、ソリューション全体をデバッグすることもできます。

## <a name="configure-your-local-environment"></a>ローカル環境を構成する

Docker for Windows の最新バージョンでは、次の参考ドキュメントで説明されているように、設定が簡単なので、Docker アプリケーションの開発がこれまでよりも簡単になりました。

> [!TIP]
> Docker for Windows のインストールの詳細については、(<https://docs.docker.com/docker-for-windows/>) を参照してください。

## <a name="docker-support-in-visual-studio"></a>Visual Studio での Docker サポート

プロジェクトに追加できる Docker サポートには 2 つのレベルがあります。 ASP.NET Core プロジェクトでは、Docker サポートを有効にしてプロジェクトに `Dockerfile` ファイルを追加するだけです。 次のレベルはコンテナー オーケストレーションのサポートです。(まだ存在しない場合は) `Dockerfile` をプロジェクトに追加し、ソリューション レベルで `docker-compose.yml` ファイルを追加します。 Docker Compose によるコンテナー オーケストレーションのサポートは、Visual Studio 2017 バージョン 15.0 から 15.7 で既定で追加されています。 コンテナー オーケストレーションのサポートは、Visual Studio 2017 バージョン 15.8 以降のオプトイン機能です。 Visual Studio 2019 以降では、**Kubernetes/Helm** デプロイもサポートされています。

**[追加] > [Docker のサポート]** と **[追加] > [コンテナー オーケストレーター サポート]** コマンドは、**ソリューション エクスプローラー** の ASP.NET Core プロジェクトのプロジェクト ノードの右クリック メニュー (またはコンテキスト メニュー) にあります。図 4-31 を参照してください。

![Visual Studio の Docker サポートの追加メニュー オプション](media/add-docker-support-menu.png)

**図 4-31**。 Visual Studio 2019 プロジェクトに Docker サポートを追加する

### <a name="add-docker-support"></a>Docker サポートの追加

前のセクションに示すような、Docker サポートを既存のアプリケーションに追加するオプションに加えて、プロジェクトの作成中に Docker サポートを有効にするには、図 4-32 に示すように、 **[新しいプロジェクト]** ダイアログ ボックスで **[OK]** をクリックすると開く **[新しい ASP.NET Core Web アプリケーション]** ダイアログ ボックスで、 **[Docker サポートを有効にする]** を選択します。

![Visual Studio で新しい ASP.NET Core Web アプリの Docker サポートを有効にする](media/enable-docker-support-visual-studio.png)

**図 4-32**。 Visual Studio 2019 でプロジェクトの作成中に Docker サポートを有効にする

Docker サポートを追加または有効にすると、Visual Studio によって _Dockerfile_ ファイルがプロジェクトに追加されます。このファイルには、ソリューションからの必要なすべてのプロジェクトへの参照が含まれています。

### <a name="add-container-orchestration-support"></a>コンテナー オーケストレーションのサポートを追加する

複数コンテナーのソリューションを構成する場合は、コンテナー オーケストレーションのサポートをプロジェクトに追加します。 これにより、コンテナーのグループ (ソリューション全体) が同じ _docker-compose.yml_ ファイル内で定義されている場合、それらを同時に実行およびデバッグすることができます。

コンテナー オーケストレーションのサポートを追加するには、**ソリューション エクスプローラー** でソリューションまたはプロジェクトのノードを右クリックし、**[追加] > [Container Orchestration Support]\(コンテナー オーケストレーション サポート\)** の順に選択します。 次に、 **[Kubernetes/Helm]** または **[Docker Compose]** を選択して、コンテナーを管理します。

プロジェクトにコンテナー オーケストレーションのサポートを追加すると、図 4-33 に示すように、プロジェクトに Dockerfile が追加され、**ソリューション エクスプローラー** 内のソリューションに **docker-compose** フォルダーが追加されるのを確認できます。

![Visual Studio のソリューション エクスプローラーの Docker ファイル](media/docker-support-solution-explorer.png)

**図 4-33**。 Visual Studio 2019 のソリューション エクスプローラーの Docker ファイル

_docker-compose.yml_ が既に存在する場合、Visual Studio により、構成コードの必要な行が単にそれに追加されます。

## <a name="configure-docker-tools"></a>Docker ツールを構成する

メイン メニューから **[ツール] > [オプション]** を選択し、**[コンテナー ツール] > [設定]** を展開します。 コンテナー ツールの設定が表示されます。

![Visual Studio Docker ツールのオプションであり、3 つのページ ([全般]、[1 つのプロジェクト]、[Docker Compose])、記事のテキストに記載されている詳細を示しています。](media/visual-studio-docker-tools-options.png)

**図 4-34**. Docker ツールのオプション

これらのオプションの設定方法を判断する際に、次の表を参照してください。

| ページ/設定                                |  既定の設定   | 説明                                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------------------------------------- | :----------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **[全般] ページ**                            |
| 必要に応じて Docker Desktop をインストールします            |     プロンプトを表示する      |
| 必要に応じて Docker Desktop を開始します              |     プロンプトを表示する      |
| ASP.NET Core SSL 証明書を信頼する          |     プロンプトを表示する      | localhost SSL 証明書が信頼済み (`dotnet dev-certs https --trust`) としてマークされていない場合、プロジェクトを実行するたびに Visual Studio によって確認メッセージが表示されます。                                                                                                                                                                                                                                                    |
| **[1 つのプロジェクト] ページ**                     |
| プロジェクトを開く際に必要な Docker イメージをプルします |        True        | プロジェクトを実行するときのパフォーマンスを向上させるために、Visual Studio ではバックグラウンドで Docker のプル操作が開始されます。そのため、コードを実行する準備ができたときには、イメージは既にダウンロードされているかダウンロード中です。 プロジェクトを読み込んでコードを参照するだけの場合は、これをオフにして不要なコンテナー イメージをダウンロードしないようにすることができます。 これにより、ユーザーがプロジェクトを開く操作を行うのに時間がかかる可能性があります。 |
| 更新された Docker イメージを、プロジェクトを読み込むときにプルする  | .NET Core プロジェクト | 既存のイメージに対する更新をプルして、プロジェクトを開くときに最新の更新プログラムを取得します。 これにより、ユーザーがプロジェクトを開く操作を行うのに時間がかかる可能性があります。                                                                                                                                                                                                                                                                                          |
| プロジェクトを閉じるときにコンテナーを削除する          |        True        | プロジェクトを閉じるときにクリーンアップします。これにより、ユーザーがプロジェクトを閉じる操作を行うのに時間がかかる可能性がありますが、通常はすばやく行われます。                                                                                                                                                                                                                                                                                                            |
| プロジェクトを開くときにコンテナーを実行する              |        True        | プロジェクトを実行するときのパフォーマンスを向上させるために、Visual Studio によってソリューション内のすべてのコンテナーの起動が行われます。 これにより、ユーザーがプロジェクトを開く操作を行うのに時間がかかる可能性があります。                                                                                                                                                                                                                                                        |
| **Docker Compose**                          |                    | [Docker Compose] ページには、[1 つのプロジェクト] ページと同じ設定が含まれていますが、この設定は複数コンテナーのソリューションに適用されます。                                                                                                                                                                                                                                                                                           |

> [!WARNING]
> localhost SSL 証明書が信頼されていない場合にオプションを **[不可]** に設定すると、アプリまたはサービスの実行時に HTTPS Web 要求が失敗する可能性があります。 その場合は、値を **[プロンプトを表示する]** の設定に戻すか、コマンド `dotnet dev-certs https --trust` を使用して、開発用コンピューターで証明書を再度信頼します。

> [!TIP]
> サービスの実装と、Visual Studio Tools for Docker の使用方法の詳細については、以下の記事を参照してください。
>
> ローカルの Docker コンテナーでのアプリのデバッグ (<https://docs.microsoft.com/visualstudio/containers/edit-and-refresh>)
>
> Visual Studio を使用して ASP.NET Docker コンテナーをコンテナー レジストリにデプロイする: <https://docs.microsoft.com/visualstudio/containers/hosting-web-apps-in-docker>

> [!div class="step-by-step"]
> [前へ](docker-apps-inner-loop-workflow.md)
> [次へ](set-up-windows-containers-with-powershell.md)
