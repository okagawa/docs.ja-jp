---
title: Azure SDK for .NET の概要
description: Azure SDK for .NET の概要と、.NET アプリケーションで SDK を使用するための基本的な手順を示します。
ms.date: 11/30/2020
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: b547e105b13d380ffae049ab55e76aa25abe8cc3
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189201"
---
# <a name="azure-sdk-for-net-overview"></a>Azure SDK for .NET の概要

## <a name="what-is-the-azure-sdk-for-net"></a>Azure SDK for .NET とは

**Azure SDK for .NET** は、.NET アプリケーションから Azure サービスを簡単に使用できるように設計されています。  BLOB ストレージにファイルをアップロードおよびダウンロードする場合も、Azure Key Vault からアプリケーション シークレットを取得する場合も、Azure Event Hubs からの通知を処理する場合も、Azure SDK for .NET では、Azure サービスにアクセスするための一貫性のある使いやすいインターフェイスが提供されます。  

Azure SDK for .NET は、.NET Core (2.1 以降) と .NET Framework (4.6.1 以上) のアプリケーションの両方で使用できる一連の NuGet パッケージとして提供されています。

![.NET アプリケーションで Azure SDK を使用して Azure サービスにアクセスする方法を示す図](./media/azure-sdk-for-dotnet-overview.png)

## <a name="use-the-azure-sdk-for-net-in-your-applications"></a>アプリケーションで Azure SDK for .NET を使用する

いずれかの .NET アプリケーションで Azure SDK パッケージを使用するには、次の手順を実行します。

1. **適切な SDK パッケージを見つける -** [パッケージの一覧](../packages.md)を使用して、使用している Azure サービスに適したパッケージを見つけます。  ほとんどのサービスには、サービスを使用するためのクライアント パッケージと、サービスのインスタンスを作成および管理するための管理パッケージがあります。  ほとんどの場合、クライアント パッケージが必要になります。  NuGet を使用して、このパッケージをアプリケーションにインストールします。

2. **アプリケーションの認証を設定する -** Azure リソースにアクセスするには、Azure でアプリケーションに適切な資格情報とアクセス権が割り当てられている必要があります。  認証を構成する方法については、[Azure への .NET アプリケーションの認証](../authentication.md)に関するページを参照してください。

3. **アプリケーションで SDK を使用してコードを記述する -** Azure サービスを使用する場合は、コードによって、まずサービスと連携するクライアント オブジェクトが作成されてから、そのクライアント オブジェクトでサービスとやり取りするためのメソッドが呼び出されます。  同期メソッドと非同期メソッドの両方が用意されています。  個々の SDK パッケージを使用する例については、Azure ドキュメントを参照してください。

4. **SDK のログを構成する (省略可能) -** アプリケーションと Azure の間の問題を診断する必要がある場合は、[Azure SDK for .NET でログを有効にする](../logging.md)ことができます。
