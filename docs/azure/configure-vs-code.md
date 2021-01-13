---
title: .NET を使用して Azure 開発用に Visual Studio Code を構成する
description: この記事は、VS Code で適切なプラグインをインストールして構成するなど、Azure 開発用に Visual Studio Code を構成するのに役立ちます
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 65ced99befe12d137062b4ea6a59a1ccd3099e0b
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700988"
---
# <a name="configure-visual-studio-code-for-azure-development"></a>Azure 開発用に Visual Studio Code を構成する

.NET 開発のため、Angular、React、Vue などのフレームワークを使用したシングル ページ アプリケーションをビルドするため、または Python などの別の言語でのアプリケーションを作成するためかどうかに関係なく、Visual Studio Code を使用している場合は、Azure 開発用に Visual Studio Code を構成する必要があります。

### <a name="download-visual-studio-code"></a>Visual Studio Code をダウンロードする

既に Visual Studio Code をインストールしている場合、この手順は省略できます

> [!div class="nextstepaction"]
> [Visual Studio Code をダウンロードする](https://code.visualstudio.com/download)

### <a name="install-the-azure-tools-extension-pack"></a>Azure Tools 拡張機能パックをインストールする

[Azure Tools 拡張機能パック](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)は、Azure App Service、Azure Functions、Azure Storage、Cosmos DB、Azure Virtual Machines を使用するためのすべての拡張機能を 1 つの便利なパッケージに収めたものです。

Visual Studio Code から拡張機能をインストールするには:

1. <kbd>Ctrl + Shift + X</kbd> キーを押して、 **[拡張機能]** ウィンドウを開きます。
1. *Azure Tools* 拡張機能を検索します。
1. **[インストール]** ボタンを選択します。

![Azure Tools 拡張機能パックを検索している拡張機能パネルを示している Visual Studio Code のスクリーンショット](./media/visual-studio-code-azure-tools.png)

Visual Studio Code に拡張機能をインストールする方法の詳細については、Visual Studio Code Web サイトの「[Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery)」のドキュメントを参照してください。

### <a name="sign-in-to-your-azure-account-with-azure-tools"></a>Azure Tools を使用して Azure アカウントにサインインする

左側のパネルに、Azure アイコンが表示されます。 このアイコンを選択すると、Azure サービスのコントロール パネルが表示されます。 任意のサービスの下で **[Azure にサインイン]** を選択して、Visual Studio Code で Azure Tools の認証プロセスを完了します。

![Azure Tools を Azure にログインする方法を示している Visual Studio Code のスクリーンショット](./media/visual-studio-code-azure-login.png)

### <a name="next-steps"></a>次のステップ

次は、Azure CLI をワークステーションにインストールします。

> [!div class="nextstepaction"]
> [Azure CLI のインストール](./install-azure-cli.md)
