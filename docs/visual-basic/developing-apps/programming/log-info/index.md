---
title: アプリケーションからの情報のログ記録
ms.date: 07/20/2015
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
ms.openlocfilehash: 43738b2d654435532a98654cbc40af134d43f02c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410024"
---
# <a name="logging-information-from-the-application-visual-basic"></a>アプリケーションからの情報のログ記録 (Visual Basic)

このセクションには、`My.Application.Log` オブジェクトまたは `My.Log` オブジェクトを使ってアプリケーションの情報を記録する方法と、アプリケーションのログ機能を拡張する方法に関するトピックが含まれます。  
  
 `Log` オブジェクトはアプリケーションのログ リスナーに情報を書き込むためのメソッドを提供し、`Log` オブジェクトの高度な `TraceSource` プロパティは詳細な構成情報を提供します。 `Log` オブジェクトは、アプリケーションの構成ファイルによって構成されます。  
  
 `My.Log` オブジェクトは、ASP.NET アプリケーションでのみ使うことができます。 クライアント アプリケーションの場合は `My.Application.Log` を使います。 詳細については、「<xref:Microsoft.VisualBasic.Logging.Log>」を参照してください。  
  
## <a name="tasks"></a>タスク  
  
|終了|解決方法については、|  
|--------|---------|  
|イベントの情報をアプリケーションのログに書き込みます。|[方法: ログ メッセージを書き込む](how-to-write-log-messages.md)|  
|例外の情報をアプリケーションのログに書き込みます。|[方法: 例外をログに記録する](how-to-log-exceptions.md)|  
|アプリケーションの起動時または終了時に、トレース情報をアプリケーションのログに書き込みます。|[方法: アプリケーションの起動時または終了時にメッセージをログに記録する](how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|テキスト ファイルに情報を書き込むように `My.Application.Log` を構成します。|[方法: イベント情報をテキスト ファイルに書き込む](how-to-write-event-information-to-a-text-file.md)|  
|イベント ログに情報を書き込むように `My.Application.Log` を構成します。|[方法: アプリケーション イベント ログに書き込む](how-to-write-to-an-application-event-log.md)|  
|`My.Application.Log` が情報を書き込む場所を変更します。|[チュートリアル: My.Application.Log による情報の書き込み先の変更](walkthrough-changing-where-my-application-log-writes-information.md)|  
|`My.Application.Log` が情報を書き込む場所を取得します。|[チュートリアル: My.Application.Log による情報の書き込み先の確認](walkthrough-determining-where-my-application-log-writes-information.md)|  
|`My.Application.Log` のカスタム ログ リスナーを作成します。|[チュートリアル: カスタム ログ リスナーの作成](walkthrough-creating-custom-log-listeners.md)|  
|`My.Application.Log` ログの出力をフィルター処理します。|[チュートリアル: My.Application.Log の出力をフィルター処理する](walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [アプリケーション ログの使用](working-with-application-logs.md)
- [トラブルシューティング : ログ リスナー](troubleshooting-log-listeners.md)
