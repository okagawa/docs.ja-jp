---
title: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
description: Docker および Microsoft のプラットフォームとツールでコンテナー化されたアプリケーションを開発およびデプロイするための、開発とデプロイのプロセスの概要を説明します。
ms.date: 11/10/2020
ms.openlocfilehash: cf20ea97ec252649cdb14add40ead67b6319520a
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506663"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a>Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル

![本の表紙](./media/devops-book-cover-large-we.png)

**エディション v3.1** - ASP.NET Core 3.1 に更新

書籍の更新とコミュニティへの投稿については、「[changelog](https://aka.ms/DockerLifecycleEbookChangelog)」を参照してください。

このガイドは、Microsoft のプラットフォームとツールを使用して、コンテナー化された ASP.NET Core アプリケーションを Docker で開発およびデプロイするための一般的な概要です。 このガイドには、CI/CD パイプラインを実装するための Azure DevOps の概要、Azure Container Registry (ACR)、デプロイ用の Azure Kubernetes Services AKS が含まれています。

開発に関連した低レベルの詳細については、『[.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ](../microservices/index.md)』 ガイドと IT 関連の参照アプリケーション [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) をご覧ください。

## <a name="send-us-your-feedback"></a>フィードバックをお寄せください。

このガイドは、コンテナー化されたアプリケーションと .NET のマイクロサービスのアーキテクチャの理解を促進する目的で書かれています。 ガイドと関連する参照アプリケーションは進化していくため、お客様のフィードバックをお待ちしています。 このガイドを改善する方法に関するコメントがある場合は、<https://aka.ms/ebookfeedback> にフィードバックを送信してください。

## <a name="credits"></a>謝辞

作成者:

> **Cesar de la Torre** 、Microsoft Corp.、.NET 製品チーム、シニア PM

総合編集者:

> **Janine Patrick**

監修者:

> **Bob Russell** 、Microsoft、ソリューション プロフェッショナル
>
> [**Octal Publishing, Inc.**](http://www.octalpub.com/)

制作者:

> [Dianne Russell](http://www.octalpub.com/)
>
> **Octal Publishing, Inc.**

原稿整理編集者:

> **Bob Russell** 、Microsoft、ソリューション プロフェッショナル

参加者とレビュー担当者:

> **Nish Anil** 、Microsoft、.NET チーム、シニア プログラム マネージャー
>
> **Miguel Veloso** 、Plain Concepts のソフトウェア開発エンジニア
>
> **Sumit Ghosh** 、Neudesic、主席コンサルタント

## <a name="copyright"></a>Copyright

発行者

Microsoft 開発部門、.NET および Visual Studio 製品チーム

A division of Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright &copy; 2020 by Microsoft Corporation

All rights reserved. 本書のいかなる部分も、書面による発行者の許可なしに、いかなる形式または方法によっても、複製または伝送することを禁じます。

本書は "現状有姿" で提供され、著者の見解と意見を表しています。 URL および他の参照されているインターネットの Web サイトをはじめ、本書に記載されている見解、意見、および情報は、通知なく変更されることがあります。

ここに記載したいくつかの例は、説明のためだけに提供された架空のものです。 実在のものとの関連性または関係性は一切ありません。

<https://www.microsoft.com> の "商標" Web ページに記載されている Microsoft および商標は、Microsoft グループの商標です。

Mac および macOS は Apple Inc. の商標です。

Docker のクジラのロゴは Docker, Inc. の登録商標です。許可を得て使用しています。

その他のすべてのマークおよびロゴは、該当する各社が所有しています。

>[!div class="step-by-step"]
>[次へ](introduction-to-containers-and-docker.md)
