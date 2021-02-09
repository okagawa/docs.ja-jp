---
description: '詳細情報: 単一インスタンスのスタートアップに必要なオペレーティング システムのリソースが取得できないため、予期しないエラーが発生しました。'
title: 単一インスタンスのスタートアップに必要なオペレーティング システムのリソースが取得できないため、予期しないエラーが発生しました。
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 43ac84e053def32cd5fa0dfc798bd47a022c0471
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797173"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a>単一インスタンスのスタートアップに必要なオペレーティング システムのリソースが取得できないため、予期しないエラーが発生しました。

アプリケーションは、必要なオペレーティング システムのリソースを取得できませんでした。 この問題の考えられる原因の一部は次のとおりです。  
  
- 指定されたオペレーティング システム オブジェクトを作成するためのアクセス許可がアプリケーションにない。  
  
- メモリ マップト ファイルを作成するためのアクセス許可が共通言語ランタイムにない。  
  
- アプリケーションからオペレーティング システム オブジェクトにアクセスする必要があるが、別のプロセスがそれを使用している。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 指定されたオペレーティング システム オブジェクトを作成するための十分なアクセス許可がアプリケーションにあることを確認します。  
  
2. メモリ マップト ファイルを作成するための十分なアクセス許可が共通言語ランタイムにあることを確認します。  
  
3. コンピューターを再起動して、元のインスタンス アプリケーションへの接続に必要なリソースを使用している可能性のあるプロセスをすべて削除します。  
  
4. エラーが発生した状況を記録して、マイクロソフト プロダクト サポート サービスにご連絡ください。  
  
## <a name="see-also"></a>関連項目

- [[アプリケーション] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [デバッガーの基本事項](/visualstudio/debugger/debugger-basics)
- [ご意見](/visualstudio/ide/feedback-options)
