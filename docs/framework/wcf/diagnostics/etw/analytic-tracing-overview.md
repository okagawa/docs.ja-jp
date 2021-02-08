---
description: 詳細については、「分析トレースの概要」を参照してください。
title: 分析トレースの概要
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
ms.openlocfilehash: 574236b364ab03afbf3c1f3dc3a63842220e38b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798863"
---
# <a name="analytic-tracing-overview"></a>分析トレースの概要

[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] の分析トレースは、Event Tracing for Windows (ETW) を基盤とするトレース機能のセットです。詳細度は低いのですが、パフォーマンスに優れています。 ETW は、カーネル レベルで実行され、トレース操作のオーバーヘッドを大幅に削減します。 ユーザー モードおよびカーネル モードのイベントを効率よくバッファーし、サービスの再起動を必要とすることなく、動的にログを有効化できます。 トレース データは、生成および受信されると、イベント ログから確認できます。

ETW の詳細については、「 [etw を使用したデバッグとパフォーマンスチューニングの向上](/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)」を参照してください。

 Windows システム、セキュリティ、およびアプリケーションのイベントログを使用してアプリケーションを分析するだけでなく、Windows Vista および Windows Server 2008 では、[アプリケーションとサービスログ] の最上位ノードに追加のログが導入されました。 これらの新しいログは、システム全体に影響するグローバルなイベント (セキュリティ イベント ログで記録されるようなイベントなど) ではなく、特定のアプリケーションやコンポーネントのイベントを格納することを目的としています。 [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] WCF トレースイベント、WCF メッセージログ、および追跡レコードのログ記録 [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] を、アプリケーションとサービスログに統合して関連付けます。

以下のセクションでは、WCF 分析トレースに適用される概念と機能について説明します。

## <a name="enable-wcf-diagnostics-settings"></a>WCF 診断設定を有効にする

WCF 診断は、構成セクション内で有効になってい `<system.serviceModel><diagnostics>` ます。

```xml
<system.serviceModel>
  <diagnostics>
```

Web でホストされる IIS 仮想アプリケーションの WCF 診断設定は、その *Web.config* ファイルで有効になります。 別の方法として、アプリケーション内のサブディレクトリに *Web.config* ファイルを作成することもできます。 このオプションを選択すると、サブディレクトリ内のすべてのサービスに設定が適用されます。 診断設定がアプリケーション内のすべてのサービスに対して一貫して初期化されるようにするには、アプリケーション内の個々のサブディレクトリの1つではなく、アプリケーションディレクトリ内の *Web.config* ファイル内に設定を配置する必要があります。

## <a name="channels"></a>チャネル

ETW の場合、ソフトウェア コンポーネントは、チャネルを使用することで、トレース イベントをユーザーの種類に応じて振り分けることができます。 たとえば、システム管理者のイベントを1つのチャネルに送信し、アプリケーション開発者にとって重要なイベントを別のチャネルに送信できます。 チャネルには名前が付けられ、Windows に登録されるため、コンシューマーはイベントビューアーを使用してチャネルのイベントを表示できます。

 WCF の分析トレース機能は、では、 [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] Microsoft-Windows-Application-Server-Applications チャネルに書き込みます。 このチャネルは、運用環境で WCF サービスの正常性を監視する必要があるユーザー向けに設計されています。 多くの正常性の監視とトラブルシューティングのシナリオで使用できる少数のイベントを定義します。

 メッセージがイベント ログで正常にデコードされるように Event Tracing for Windows マニファストを有効にするために、次のようにコマンド ラインで ServiceModelReg ツールを使用します。

 `ServiceModelReg.exe -i -c:etw`

## <a name="dynamic-configuration"></a>動的構成

ETW のインフラストラクチャでは、標準の Windows ツールを使用して動的にトレースを有効化および構成できます。 詳細については、「 [分析トレースの動的な有効化](dynamically-enabling-analytic-tracing.md)」を参照してください。

## <a name="message-flow-tracing"></a>メッセージ フローのトレース

メッセージフローのトレースを有効にする方法の詳細については、「 [メッセージフローのトレースの構成](configuring-message-flow-tracing.md)」を参照してください。

## <a name="keywords"></a>Keywords

キーワードは、トレースメッセージをフィルター処理し、イベントを生成した .NET Framework のコンポーネントを定義するために使用されます。 詳細については、「 [分析トレースの動的な有効化](dynamically-enabling-analytic-tracing.md)」を参照してください。
