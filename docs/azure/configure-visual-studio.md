---
title: .NET を使用して Azure 開発用に Visual Studio を構成する
description: この記事は、Azure 開発用に Visual Studio を構成するのに役立ちます。これには、適切なワークロードのインストールや、Visual Studio の Azure アカウントへの接続が含まれます
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 986469bd07657d968045465803047dc21d76dd62
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700995"
---
# <a name="configure-visual-studio-for-azure-development-with-net"></a>.NET を使用して Azure 開発用に Visual Studio を構成する

Visual Studio には、Azure でのアプリケーションの開発とデプロイに役立つツールが含まれています。  このガイドは、Azure 開発用に Visual Studio が適切に構成されていることを確認するのに役立ちます。

### <a name="download-visual-studio-2019"></a>Visual Studio 2019 のダウンロード

既に Visual Studio 2019 がインストールされている場合、この手順は省略できます。

> [!div class="nextstepaction"]
> [Visual Studio 2019 のダウンロード](https://www.visualstudio.com/downloads/)

### <a name="install-azure-workloads"></a>Azure ワークロードのインストール

**Visual Studio インストーラー** を起動し、ワークロード **Azure 開発** および **ASP.NET と Web 開発** がインストールされていることを確認します。  これらのワークロードのいずれかがインストールされていない場合は、これらのワークロードを選択してインストールします。

![選択された Azure 開発および ASP.NET と Web 開発のワークロードが選択されている Visual Studio インストーラーのスクリーンショット](./media/visual-studio-installer-azure-development.png)

### <a name="authenticate-visual-studio-with-azure"></a>Azure を使用して Visual Studio を認証する

Visual Studio を使用してアプリをデバッグすると、Visual Studio では Azure アカウントを使用して Azure リソースの認証とアクセスが行われます。  このアカウントは、Visual Studio から Azure にアプリを直接発行する場合にも使用されます。

Visual Studio から Azure アカウントを認証するには、 **[ツール]**  >  **[オプション]** メニューを選択し、 **[オプション]** ダイアログを起動します。 `Azure Service Authentication` オプションに移動し、Azure アカウントを使用してサインインします。

![Azure ログインを示している Visual Studio の [オプション] ダイアログのスクリーンショット](./media/visual-studio-azure-login-dialog.png)

### <a name="next-steps"></a>次のステップ

.NET またはその他の言語での開発にも [Visual Studio Code](https://code.visualstudio.com/) を使用する場合は、[Azure 開発用に Visual Studio Code を構成](./configure-vs-code.md)する必要もあります。 それ以外の場合は、[Azure CLI のインストール](./install-azure-cli.md)に進みます。
