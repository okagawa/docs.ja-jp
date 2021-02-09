---
description: '詳細情報: ファイルが見つかりません。(Visual Basic ランタイム エラー)'
title: ファイルが見つかりません。(Visual Basic ランタイム エラー)
ms.date: 07/20/2015
f1_keywords:
- vbrID53
ms.assetid: 57addb16-6f9a-444d-8af8-dda52431daca
ms.openlocfilehash: da249093a18936a94099b3d5b727e666597f5b6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796263"
---
# <a name="file-not-found-visual-basic-run-time-error"></a>ファイルが見つかりません。(Visual Basic ランタイム エラー)

指定された場所でファイルが見つかりませんでした。 このエラーには、次のような原因が考えられます。

- ステートメントが、存在しないファイルを参照しています。

- ダイナミック リンク ライブラリ (DLL) でプロシージャを呼び出そうとしましたが、`Declare` ステートメントの `Lib` 句で指定されたライブラリが見つかりませんでした。

- プロジェクトを開こうとしたか、存在しないテキスト ファイルを読み込もうとしました。

## <a name="to-correct-this-error"></a>このエラーを解決するには

- ファイル名とパスの指定のスペルを確認してください。

## <a name="see-also"></a>関連項目

- [Declare ステートメント](../statements/declare-statement.md)
