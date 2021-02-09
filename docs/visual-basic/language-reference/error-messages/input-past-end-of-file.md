---
description: '詳細情報: ファイルにこれ以上データがありません。'
title: ファイルにこれ以上データがありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: b65a57bdc56367518a93880be28781e56c9b99cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796042"
---
# <a name="input-past-end-of-file"></a>ファイルにこれ以上データがありません。

`Input` ステートメントが空のファイル、またはすべてのデータが使用されているファイルから読み取っているか、またはバイナリ アクセス用に開かれたファイルで `EOF` 関数を使用しました。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. `Input` ステートメントの直前で `EOF` 関数を使用して、ファイルの末尾を検出します。  
  
2. ファイルがバイナリ アクセス用に開かれている場合は、`Seek` と `Loc` を使用します。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
