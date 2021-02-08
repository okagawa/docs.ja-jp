---
description: '詳細情報: 別のイベントログがこの名前のソースを既に登録しています'
title: 別のイベント ログが、既にこの名前のソースを登録しています
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: ec6ae0b3ef12452a0135e5bf17dbdd5844c0f478
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787358"
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>別のイベント ログが、既にこの名前のソースを登録しています

イベント ログにエントリを書き込もうとしましたが、指定のソースは別のイベント ログに登録されています。  
  
 <xref:System.Diagnostics.EventLog.Source%2A> コンポーネントのインスタンスの <xref:System.Diagnostics.EventLog> プロパティを設定しておかなければ、コンポーネントはログにエントリを書き込めません。 書き込み時、システムは、指定したソースがコンポーネントの書き込み先のイベント ログに登録されているかどうかを確認し、必要に応じて <xref:System.Diagnostics.EventLog.CreateEventSource%2A> を呼び出します。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> または <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> メソッドを使用して、最初のログに対するソースの関連付けを削除します。  
  
2. ソースを新しいログに登録します。  
  
## <a name="see-also"></a>関連項目

- [.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
