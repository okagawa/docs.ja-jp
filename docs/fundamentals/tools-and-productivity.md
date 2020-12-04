---
title: .NET のツールと診断
author: IEvangelist
description: .NET 開発者が使用できる開発ツールと診断ツールについて説明します。
ms.author: dapine
ms.date: 10/21/2020
ms.topic: overview
ms.openlocfilehash: 07c1a161a0bb429403db6852fe77749d83c19ec0
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2020
ms.locfileid: "96593833"
---
# <a name="tools-and-diagnostics-in-net"></a>.NET のツールと診断

この記事では、.NET 開発者が使用できるさまざまなツールについて説明します。 .NET には、コマンドラインインターフェイス (CLI) を備えた堅牢なソフトウェア開発キット (SDK) があります。 .NET CLI では、の多くの機能が有効になります。NET ready の統合開発環境 (Ide)。 この記事では、パフォーマンスの問題を診断するための .NET CLI ツール、メモリリーク、高 CPU、デッドロック、コード分析のためのツールサポートなど、生産性機能に関するリソースも提供します。

## <a name="net-sdk"></a>.NET SDK

.Net SDK には、.NET ランタイムと .NET CLI の両方が含まれています。 Windows、Linux、macOS、または Docker 用の [.NET SDK](https://dotnet.microsoft.com/download) をダウンロードできます。 詳細については、「 [.NET SDK の概要](../core/sdk.md)」を参照してください。

## <a name="net-cli"></a>.NET CLI

.NET CLI は、.NET アプリケーションを開発、ビルド、実行、および発行するためのクロスプラットフォームツールチェーンです。 .NET CLI は、.NET SDK に含まれています。 詳細については、「 [.NET CLI の概要](../core/tools/index.md)」を参照してください。

## <a name="ides"></a>IDE

.NET アプリケーションは、 [Visual Studio Code](https://code.visualstudio.com/docs)、 [Visual Studio](/visualstudio/windows)、または [Visual Studio for Mac](/visualstudio/mac)で作成できます。 クラウドを利用した開発環境の詳細については、「 [Visual Studio Codespaces](/visualstudio/codespaces/overview/what-is-vsonline)」を参照してください。

## <a name="additional-tools"></a>その他のツール

.NET では、より一般的なツールだけでなく、特定のシナリオ用のツールも用意されています。 一部のユースケースには、.NET SDK または .NET ランタイムのアンインストール、Windows Communication Foundation (WCF) メタデータの取得、プロキシソースコードの生成、XML のシリアル化などがあります。 詳細については、「 [.net の追加ツールの概要](../core/additional-tools/index.md)」を参照してください。

## <a name="diagnostics-and-instrumentation"></a>診断とインストルメンテーション

.NET 開発者は、一般的なパフォーマンス診断ツールを利用して、アプリのパフォーマンスの監視、トレースによるアプリのプロファイリング、パフォーマンスメトリックの収集、およびダンプファイルの分析を行うことができます。 イベントカウンターを使用してパフォーマンスメトリックを収集し、プロファイリングツールを使用して、アプリの動作についての洞察を得ることができます。 詳細については、「 [.net 診断ツール](../core/diagnostics/index.md)」を参照してください。

## <a name="code-analysis"></a>コード分析

.NET compiler platform (Roslyn) アナライザーは、コード品質とコードスタイルの問題について、C# または Visual Basic コードを検査します。 詳細については、「 [.net ソースコード分析の概要](code-analysis/overview.md)」を参照してください。
