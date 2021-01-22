---
title: 意思決定テーブル。 Docker に使用する .NET Frameworks
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | 意思決定テーブル、Docker に使用する .NET Frameworks'
ms.date: 01/13/2021
ms.openlocfilehash: 35f101b3f4030e081068677b3754363bf6cd8210
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188661"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>意思決定テーブル: Docker に使用する .NET Frameworks

次の意思決定テーブルは、.NET Framework と .NET 5 のどちらを使用するかをまとめたものです。 Linux コンテナーには、Linux ベースの Docker ホスト (VM またはサーバー) が必要であり、Windows コンテナーには、Windows Server ベースの Docker ホスト (VM またはサーバー) が必要であることを覚えておいてください。

> [!IMPORTANT]
> 開発用のコンピューターは、Linux または Windows の Docker ホストを 1 つ実行します。 1 つのソリューションで同時に実行してテストしたい関連するマイクロサービスは、同じコンテナー プラットフォームで実行する必要があります。

| アーキテクチャ/アプリの種類 | Linux コンテナー | Windows コンテナー |
|-------------------------|------------------|--------------------|
| コンテナー上のマイクロサービス | .NET 5 | .NET 5 |
| モノリシック アプリ | .NET 5 | .NET Framework <br/> .NET 5 |
| クラス最高のパフォーマンスとスケーラビリティ | .NET 5 | .NET 5 |
| Windows Server レガシー アプリ ("ブラウンフィールド") のコンテナーへの移行 | -- | .NET Framework |
| コンテナー ベースの新しい開発 ("グリーンフィールド") | .NET 5 | .NET 5 |
| ASP.NET Core | .NET 5 | .NET 5 (推奨) <br/> .NET Framework |
| ASP.NET 4 (MVC 5、Web API 2、Web Forms) | -- | .NET Framework |
| SignalR サービス | .NET Core 2.1 以降のバージョン | .NET Framework <br/> .NET Core 2.1 以降のバージョン |
| WCF、WF などのレガシ フレームワーク | .NET Core の WCF (クライアント ライブラリのみ) | .NET Framework <br/> .NET 5 の WCF (クライアント ライブラリのみ) |
| Azure サービスの使用 | .NET 5 <br/> (いずれ、ほとんどの Azure サービスで .NET 5 用のクライアント SDK が提供される予定です) | .NET Framework <br/> .NET 5 <br/> (いずれ、ほとんどの Azure サービスで .NET 5 用のクライアント SDK が提供される予定です) |

>[!div class="step-by-step"]
>[前へ](net-framework-container-scenarios.md)
>[次へ](net-container-os-targets.md)
