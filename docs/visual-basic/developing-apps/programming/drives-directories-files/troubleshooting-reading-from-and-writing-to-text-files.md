---
title: 'トラブルシューティング: テキスト ファイルの読み取りと書き込み'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: 8af4160d09f39f2622a007aef793173d614a8b44
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406626"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a>トラブルシューティング: テキスト ファイルの読み取りと書き込み (Visual Basic)

このトピックでは、テキスト ファイルを使用するときに発生する一般的な問題について説明し、それぞれの対処方法を示します。  
  
## <a name="common-problems"></a>一般的な問題  

 テキスト ファイルを使用するときに特によく発生する問題として、セキュリティ例外、ファイル エンコーディング、無効なパスがあります。  
  
### <a name="security-exceptions"></a>セキュリティ例外  

 セキュリティ エラーが発生した場合、<xref:System.Security.SecurityException> がスローされます。 この問題は、多くの場合、ユーザーに必要なアクセス許可がないことが原因で発生するため、アクセス許可を追加するか、分離ストレージでファイルを操作することで解決できます。  
  
### <a name="file-encodings"></a>ファイル エンコーディング  

 ファイル エンコーディングは、文字エンコーディングとも呼ばれ、テキストを処理するときの文字の表現方法を指定します。 エンコーディングが誤っていると、テキスト ファイルに予期しない文字が含まれることがあります。 ほとんどのファイルで、言語で処理できる (または処理できない) 文字という観点から、あるエンコードが他のエンコーディングよりも望ましいということがありますが、一般的には Unicode が好まれます。 詳細については、[ファイル エンコーディング](file-encodings.md) および <xref:System.Text.Encoding> に関する各記事を参照してください。  
  
### <a name="incorrect-paths"></a>無効なパス  

 ファイル パス (特に相対パス) を解析するときに、間違ったデータを指定してしまうことがよくあります。 正しいパスを指定しているかどうかを確認することで、問題の多くを解決できます。 詳細については、「[方法: ファイル パスを解析する](how-to-parse-file-paths.md)」を参照してください。  
  
## <a name="see-also"></a>参照

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [ファイルの読み取り](reading-from-files.md)
- [ファイルへの書き込み](writing-to-files.md)
- [TextFieldParser オブジェクトによるテキスト ファイルの解析](parsing-text-files-with-the-textfieldparser-object.md)
