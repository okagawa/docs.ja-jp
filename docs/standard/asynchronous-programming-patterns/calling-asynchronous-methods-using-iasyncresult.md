---
title: IAsyncResult を使用した非同期メソッドの呼び出し
ms.date: 03/30/2017
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 20aafd45c323a609b3cc7fb5a1a6378d43548fcb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830455"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a>IAsyncResult を使用した非同期メソッドの呼び出し

.NET ライブラリとサードパーティのクラス ライブラリの型では、アプリケーションのメイン スレッド以外のスレッドで非同期操作を実行しながら、アプリケーションを実行し続けることを許可するメソッドを提供できます。 次のセクションでは、コード例を取り上げ、<xref:System.IAsyncResult> 設計パターンを使用する非同期メソッドをさまざまな方法で呼び出します。  
  
- [非同期操作の終了によるアプリケーション実行のブロック](blocking-application-execution-by-ending-an-async-operation.md)。  
  
- [AsyncWaitHandle の使用によるアプリケーション実行のブロック](blocking-application-execution-using-an-asyncwaithandle.md)。  
  
- [非同期操作のステータスのポーリング](polling-for-the-status-of-an-asynchronous-operation.md)。  
  
- [AsyncCallback デリゲートの使用による非同期操作の終了](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)。  
  
## <a name="see-also"></a>参照

- [イベント ベースの非同期パターン (EAP)](event-based-asynchronous-pattern-eap.md)
- [イベントベースの非同期パターンの概要](event-based-asynchronous-pattern-overview.md)
