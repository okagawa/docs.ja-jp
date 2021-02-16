---
description: '詳細情報: Visual Basic の名前付け規則'
title: 命名規則
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: 058d3b06ca1da71c4d8993c6bd451531ec758dbd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461009"
---
# <a name="visual-basic-naming-conventions"></a>Visual Basic の名前付け規則

Visual Basic アプリケーションで要素に名前を付けるときは、その名前の最初の文字を英文字またはアンダースコアにする必要があります。 ただし、アンダースコアで始まる名前は、[言語への非依存性、および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md) (CLS) に準拠していないことに注意してください。  
  
 名前付けには、次の推奨事項が適用されます。  
  
- 名前の個々の単語は大文字で始めます (例: `FindLastRecord`、`RedrawMyForm`)。  
  
- 関数名とメソッド名は動詞で始めます (例: `InitNameArray`、`CloseDialog`)。  
  
- クラス、構造体、モジュール、プロパティの名前は名詞で始めます (例: `EmployeeName`、`CarAccessory`)。  
  
- インターフェイス名はプレフィックス "I" で始め、その後に名詞または名詞句を続けるか (例: `IComponent`)、インターフェイスの動作を示す形容詞を続けます (例: `IPersistable`)。 アンダースコアは使用しないでください。また、省略形は混乱を招く可能性があるため、慎重に使用してください。  
  
- イベント ハンドラー名は、イベントの種類を示す名詞で始め、その後に "`EventHandler`" サフィックスを付けます (例: `MouseEventHandler`)。  
  
- イベント引数クラスの名前には、"`EventArgs`" サフィックスを含めます。  
  
- イベントに "前" または "後" の概念がある場合は、現在形または過去形のサフィックスを使用します (例: `ControlAdd`、`ControlAdded`)。  
  
- 長い用語や頻繁に使用される用語については、省略形を使用して名前を妥当な長さにとどめます。たとえば、"Hypertext Markup Language" ではなく、"HTML" を使用します。 一般に、低解像度に設定されたモニターでは、32 文字を超える変数名は読みにくくなります。 また、アプリケーション全体で省略形が一貫している必要があります。 プロジェクト内で "HTML" と "Hypertext Markup Language" をランダムに切り替えると、混乱が生じる可能性があります。  
  
- 外側のスコープ内の名前と同じ名前を内側のスコープで使用しないようにします。 間違った変数にアクセスすると、エラーが発生する可能性があります。 同じ名前の変数とキーワード間で競合が発生した場合は、キーワードの前に適切なタイプ ライブラリを指定して、キーワードを識別する必要があります。 たとえば、`Date` という変数がある場合、組み込み関数の `Date` は、<xref:System.DateTime.Date%2A?displayProperty=nameWithType> を呼び出すことによってのみ使用できます。  
  
## <a name="see-also"></a>関連項目

- [コード内の要素名としてのキーワード](keywords-as-element-names-in-code.md)
- [Me、My、MyBase、および MyClass](me-my-mybase-and-myclass.md)
- [宣言された要素の名前](../language-features/declared-elements/declared-element-names.md)
- [プログラム構造とコード規則](program-structure-and-code-conventions.md)
- [Visual Basic の言語リファレンス](../../language-reference/index.md)
