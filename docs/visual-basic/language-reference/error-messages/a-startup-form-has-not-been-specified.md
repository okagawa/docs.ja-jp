---
description: '詳細情報: スタートアップ フォームが指定されていません。'
title: スタートアップ フォームが指定されていません。
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 4b00890f07121ef55ce49978842010cc54aba29b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797186"
---
# <a name="a-startup-form-has-not-been-specified"></a>スタートアップ フォームが指定されていません。

アプリケーションで <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> クラスが使用されていますが、スタートアップ フォームが指定されていません。  
  
 これは、プロジェクト デザイナーで **[アプリケーション フレームワークを有効にする]** チェック ボックスがオンになっていても、 **[スタートアップ フォーム]** が指定されていない場合に発生する可能性があります。 詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. アプリケーションのスタートアップ オブジェクトを指定します。  
  
     詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。  
  
2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> メソッドをオーバーライドして、スタートアップ フォームに <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> プロパティを設定します。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [Visual Basic アプリケーション モデルの概要](../../developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
