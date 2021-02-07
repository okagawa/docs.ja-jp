---
title: Docker コンテナー用 .NET 5 と .NET Framework の選択
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | Docker コンテナー用 .NET 5 と .NET Framework の選択
ms.date: 02/02/2021
ms.openlocfilehash: 5c3d4eff00399c8a6a041daaa71cf9fe5c9d854f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665160"
---
# <a name="choosing-between-net-5-and-net-framework-for-docker-containers"></a>Docker コンテナー用 .NET 5 と .NET Framework の選択

.NET を使用してサーバー側のコンテナー化された Docker アプリケーションをビルドする場合に選択できるサポート対象のフレームワークには、[.NET Framework と .NET 5](https://dotnet.microsoft.com/download) の 2 つがあります。 それらは多数の .NET プラットフォームのコンポーネントを共有しているため、両者でコードを共有できます。 ただし、それらには基本的な違いがあり、どちらのフレームワークを使用するかは実行内容によって決まります。 このセクションでは、それぞれのフレームワークを選択する場合のガイダンスを提供します。

>[!div class="step-by-step"]
>[前へ](../container-docker-introduction/docker-containers-images-registries.md)
>[次へ](general-guidance.md)
