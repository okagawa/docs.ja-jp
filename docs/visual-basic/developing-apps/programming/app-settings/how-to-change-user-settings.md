---
description: '詳細情報: 方法:Visual Basic でユーザー設定を変更する'
title: '方法: ユーザー設定を変更する'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 3877c9fadbf1b5b79470dc9ad41fbaf8123e6770
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797862"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>方法 : Visual Basic でユーザー設定を変更する

ユーザー設定を変更するには、`My.Settings` オブジェクトにある設定のプロパティに新しい値を代入します。  
  
 `My.Settings` オブジェクトでは、各設定はプロパティとして公開されます。 プロパティ名はその設定の名前と同じで、プロパティの型は設定の型と同じです。 プロパティが読み取り専用かどうかは、設定の **スコープ** でわかります。つまり、**アプリケーション** スコープの設定のプロパティは読み取り専用であるのに対し、**ユーザー** スコープの設定のプロパティは読み取り/書き込みです。 詳細については、「[My.Settings オブジェクト](../../../language-reference/objects/my-settings-object.md)」を参照してください。  
  
> [!NOTE]
> ユーザー スコープ設定の値は実行時に変更および保存できますが、アプリケーション スコープ設定は読み取り専用であり、プログラムで変更することはできません。 アプリケーション スコープの設定を変更するには、アプリケーションを作成するときに、**プロジェクト デザイナー** を使用するか、アプリケーションの構成ファイルを編集します。 詳細については、「[アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)」を参照してください。  
  
## <a name="example"></a>例  

 この例では、`Nickname` ユーザー設定の値を変更します。  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 この例を動作させるには、アプリケーションに `String` 型の `Nickname` ユーザー設定が必要です。  
  
 アプリケーションがユーザー設定を保存するのは、アプリケーションの終了時です。 設定をすぐに保存するには、`My.Settings.Save` メソッドを呼び出します。 詳細については、「[方法: Visual Basic でユーザー設定を永続化する](how-to-persist-user-settings.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [My.Settings オブジェクト](../../../language-reference/objects/my-settings-object.md)
- [方法: Visual Basic でアプリケーション設定を読み取る](how-to-read-application-settings.md)
- [方法: Visual Basic でユーザー設定を永続化する](how-to-persist-user-settings.md)
- [方法: Visual Basic でユーザー設定のためのプロパティ グリッドを作成する](how-to-create-property-grids-for-user-settings.md)
- [アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
