---
description: '詳細情報: 方法:ログ メッセージを書き込む (Visual Basic)'
title: '方法: ログ メッセージを書き込む'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: ed455fdb2cebda908981514bef932942adf499ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797303"
---
# <a name="how-to-write-log-messages-visual-basic"></a>方法: ログ メッセージを書き込む (Visual Basic)

`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーションに関する情報をログに記録できます。 この例では、 `My.Application.Log.WriteEntry` メソッドを使用してトレース情報をログに記録する方法を示します。

例外情報をログに記録するには、`My.Application.Log.WriteException` メソッドを使います。方法については、「[方法 : 例外をログに記録する](how-to-log-exceptions.md)」をご覧ください。

## <a name="example"></a>例

この例では、 `My.Application.Log.WriteEntry` メソッドを使用してトレース情報を書き込みます。

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a>.NET Framework のセキュリティ

ログに書き込むデータに、ユーザーのパスワードなどの機密情報が含まれないように注意してください。 詳しくは、「[アプリケーション ログの使用](working-with-application-logs.md)」をご覧ください。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [アプリケーション ログの使用](working-with-application-logs.md)
- [方法: 例外をログに記録する](how-to-log-exceptions.md)
- [チュートリアル : My.Application.Log による情報の書き込み先の確認](walkthrough-determining-where-my-application-log-writes-information.md)
- [チュートリアル : My.Application.Log による情報の書き込み先の変更](walkthrough-changing-where-my-application-log-writes-information.md)
- [チュートリアル: My.Application.Log の出力をフィルター処理する](walkthrough-filtering-my-application-log-output.md)
