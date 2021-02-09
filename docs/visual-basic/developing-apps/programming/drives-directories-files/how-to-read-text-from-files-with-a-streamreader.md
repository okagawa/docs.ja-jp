---
description: '詳細情報: 方法:StreamReader を使用してファイルからテキストを読み取る (Visual Basic)'
title: '方法: StreamReader を使用してファイルからテキストを読み取る'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: 9a2eb08209a2a65f7be846c8cb5357978a48ed73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797420"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a>方法: StreamReader を使用してファイルからテキストを読み取る (Visual Basic)

`My.Computer.FileSystem` オブジェクトには、<xref:System.IO.TextReader> および <xref:System.IO.TextWriter> を開くためのメソッドがあります。 これらのメソッド (`OpenTextFileWriter` メソッドと `OpenTextFileReader` メソッド) は、高度なメソッドで、**[すべて]** タブを選択しないと IntelliSense で表示されません。  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a>テキスト リーダーを使用してファイルから行を読み取るには  
  
- `OpenTextFileReader` メソッドにファイルを指定して <xref:System.IO.TextReader> を開きます。 この例では、`testfile.txt` という名前のファイルを開き、1 行を読み取って、その行をメッセージ ボックスに表示します。  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  

 読み取るファイルは、テキスト ファイルである必要があります。  
  
 ファイル名からファイルの内容を判断しないでください。 たとえば、Form1.vb というファイルは Visual Basic のソース ファイルではない可能性もあります。  
  
 アプリケーションでデータを使用する前に、入力をすべて検証してください。 ファイルの内容が予想どおりでないことがあり、ファイルの内容を読み取るメソッドが失敗する可能性があります。  
  
## <a name="net-framework-security"></a>.NET Framework のセキュリティ  

 ファイルを読み取るには、アセンブリに対して <xref:System.Security.Permissions.FileIOPermission> クラスで特権レベルが許可されている必要があります。 部分的に信頼されたコンテキストで実行している場合、コードは、特権がないために例外をスローする可能性があります。 詳しくは、「[コード アクセス セキュリティの基礎](../../../../framework/misc/code-access-security-basics.md)」をご覧ください。 また、ユーザーはファイルへのアクセス許可も必要です。 詳細については、「[アクセス制御リスト (ACL: Access Control List) 技術の概要](/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100))」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [SaveFileDialog コンポーネント](/dotnet/desktop/winforms/controls/savefiledialog-component-windows-forms)
- [ファイルの読み取り](reading-from-files.md)
