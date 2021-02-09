---
description: '詳細情報: ファイル モードが正しくありません。'
title: ファイル モードが正しくありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: da792407fb37f5c206be7ff39da14d314ef1e2d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797082"
---
# <a name="bad-file-mode"></a>ファイル モードが正しくありません。

ファイルの内容を操作するために使用されるステートメントは、ファイルが開かれたモードに適している必要があります。 以下の原因が考えられます。  
  
- `FilePutObject` または `FileGetObject` ステートメントがシーケンシャル ファイルを指定しています。  
  
- `Print` ステートメントが、`Output` または `Append` 以外のアクセス モード用に開かれたファイルを指定しています。  
  
- `Input` ステートメントが、`Input` 以外のアクセス モードで開かれたファイルを指定しています  
  
- 読み取り専用ファイルに書き込もうとしました。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- `FilePutObject` および `FileGetObject` が、`Random` または `Binary` アクセス用に開かれたファイルのみを参照していることを確認します。  
  
- `Print` が `Output` または `Append` アクセス モードのいずれかで開かれているファイルを指定していることを確認します。 そうでない場合は、別のステートメントを使用してファイルにデータを格納するか、適切なモードでファイルを再度開きます。  
  
- `Input` が `Input` で開かれているファイルを指定していることを確認します。 そうでない場合は、別のステートメントを使用してファイルにデータを格納するか、適切なモードでファイルを再度開きます。  
  
- 読み取り専用ファイルに書き込む場合は、ファイルの読み取り/書き込みの状態を変更するか、ファイルへの書き込みを試みないようにします。  
  
- `My.Computer.FileSystem` オブジェクトで利用できる機能を使用します。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.FileSystem>
- [トラブルシューティング : テキスト ファイルの読み取りと書き込み](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
