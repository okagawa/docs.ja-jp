---
description: '詳細情報: レジストリからの読み取りとレジストリへの書き込み (Visual Basic)'
title: レジストリからの読み取りとレジストリへの書き込み
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: 0a9e32480845e617f6e4fde2f31c58eea8da4ee7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701548"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a>レジストリからの読み取りとレジストリへの書き込み (Visual Basic)

このトピックでは、レジストリに関連するタスクおよび概念説明のトピックについて説明します。  
  
 Visual Basic のプログラミングでレジストリにアクセスするときは、Visual Basic で提供されている関数を使用するか、または.NET のレジストリ クラスを使用するかを選択できます。 レジストリは、オペレーティング システムからの情報と、コンピューターにホストされるアプリケーションからの情報をホストします。 レジストリを操作すると、システム リソースや保護情報への不適切なアクセスが許可され、セキュリティが損なわれる場合があります。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [方法: レジストリ キーを作成し、その値を設定する](how-to-create-a-registry-key-and-set-its-value.md)  
 `My.Computer.Registry` オブジェクトの `CreateSubKey` および `SetValue` メソッドを使用して、レジストリ キーを作成し、その値を設定する方法について説明します。  
  
 [方法 : レジストリ キーから値を読み取る](how-to-read-a-value-from-a-registry-key.md)  
 `My.Computer.Registry` オブジェクトの `GetValue` メソッドを使用して、レジストリ キーから値を読み取る方法について説明します。  
  
 [方法: レジストリ キーを削除する](how-to-delete-a-registry-key.md)  
 `My.Computer.Registry.CurrentUser` プロパティの `DeleteSubKey` メソッドを使用して、レジストリ キーを削除する方法について説明します。  
  
 [Microsoft.Win32 名前空間を使用したレジストリの読み取りと書き込み](reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 .NET の `Registry` および `RegistryKey` クラスを使用してレジストリにアクセスする方法について説明します。  
  
 [セキュリティとレジストリ](security-and-the-registry.md)  
 レジストリに関連するセキュリティの問題について説明します。  
  
## <a name="related-sections"></a>関連項目  

 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 `My.Computer.Registry` オブジェクトのメンバーをリストして説明します。  
  
 <xref:Microsoft.Win32.Registry>  
 `Registry` クラスの概要と、個々のキーおよびメンバーへのリンクを示します。
