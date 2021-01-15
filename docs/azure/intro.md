---
title: Azure と .NET を使用して作業を開始する
description: Azure と .NET について知っておくべき基本的事項について説明します。
ms.date: 06/20/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: b5766012b77da88ae9a696939b6e498ebc421522
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025043"
---
# <a name="introduction-to-azure-and-net"></a>Azure と .NET の概要

## <a name="what-is-azure"></a>Azure とは

Azure は、最新のアプリケーションのビルド プロセスを簡略化することを目的としたクラウド プラットフォームです。  Azure でアプリケーションを完全にホストする場合も、Azure サービスを使用してオンプレミスのアプリケーションを拡張する場合も、Azure を使用すると、スケーラブルで信頼性が高く、保守が容易なアプリケーションを作成することができます。  Visual Studio や Visual Studio Code、包括的な SDK ライブラリなど、既に使用しているツールの広範なサポートにより、Azure は、最初から .NET 開発者の生産性を向上させることを目的として設計されています。

## <a name="application-development-scenarios-on-azure"></a>Azure でのアプリケーション開発シナリオ

ニーズに応じて、さまざまな方法で Azure をアプリケーションに組み込むことができます。

- **Azure でホストされるアプリケーション -** Azure では、Web アプリケーションや API からストレージ サービス、データベースに至るまで、アプリケーション スタック全体をホストできます。 Azure では、完全に管理されたサービスからコンテナー、仮想マシンに至るまで、さまざまなホスティング モデルがサポートされています。 完全に管理された Azure サービスを使用する場合、アプリケーションでは、Azure に組み込まれているスケーラビリティ、高可用性、およびセキュリティを利用できます。

- **アプリケーションからのクラウド サービスの利用 -** 既存のアプリに Azure サービスを組み込んで、機能を拡張することができます。  これには、[Azure Cognitive Search](/azure/search/search-what-is-azure-search) によるフルテキスト検索機能の追加、[Azure Key Vault](/azure/key-vault/) でのアプリケーション シークレットの安全な格納、[Azure Cognitive Services](/azure/cognitive-services/) によるビジョン、音声認識、言語理解機能の追加などが含まれます。  これらのサービスは Azure によって完全に管理され、現在のアプリケーション アーキテクチャやデプロイ モデルを変更することなく、簡単にアプリケーションに追加できます。

- **最新のサーバーレス アーキテクチャ -** HTTP 要求に応答する場合も、BLOB ストレージでファイルのアップロードを処理する場合も、キュー内のイベントを処理する場合も、Azure Functions を使用すると、イベントドリブン ワークフローを処理するソリューションを簡単に構築できます。  サーバーやフレームワーク コードを気にせずに、イベントを処理するために必要なコードのみを記述します。  さらに、他の Azure やサードパーティのサービスに対して 250 を超えるコネクタを利用して、最も困難な統合の問題に対処することができます。

## <a name="access-azure-services-from-net-applications"></a>.NET アプリケーションから Azure サービスにアクセスする

アプリが Azure とオンプレミスのどちらでホストされている場合でも、ほとんどの Azure サービスへのアクセスは **Azure SDK for .NET** を通じて提供されます。  Azure SDK for .NET は一連の NuGet パッケージとして提供されており、.NET Core (2.1 以降) アプリケーションと .NET Framework (4.6.1 以降) アプリケーションの両方で使用できます。 Azure SDK for .NET を使用すると、適切な NuGet パッケージをインストールしたり、クライアント オブジェクトをインスタンス化したり、適切なメソッドを呼び出すのと同様に、簡単に Azure サービスをアプリケーションに組み込むことができます。 Azure SDK for .NET の詳細については、「[Azure SDK for .NET の概要](./sdk/azure-sdk-for-dotnet.md)」を参照してください。

![.NET アプリケーションで Azure SDK を使用して Azure サービスにアクセスする方法を示す図](./media/azure-sdk-for-dotnet-overview.png)

## <a name="next-steps"></a>次のステップ

次に、.NET 開発用に最も[一般的に使用される Azure サービス](./key-azure-services.md)について説明します。
