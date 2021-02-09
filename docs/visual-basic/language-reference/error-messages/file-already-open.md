---
description: '詳細情報: ファイルは既に開かれています。'
title: ファイルは既に開かれています。
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 2f3345c15f4a3095a8e733c2c8424edb25b4dee6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796302"
---
# <a name="file-already-open"></a>ファイルは既に開かれています。

別の `FileOpen` またはその他の操作を実行する前に、ファイルを閉じる必要がある場合があります。 このエラーでは以下の原因が考えられます。

- 既に開いているファイルに対して順次出力モードの `FileOpen` 操作が実行されました

- ステートメントが開いているファイルを参照しています。

## <a name="to-correct-this-error"></a>このエラーを解決するには

- ステートメントを実行する前に、ファイルを閉じます。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
