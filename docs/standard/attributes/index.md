---
title: 属性を使用したメタデータの拡張
description: .NET の属性を使用してメタデータを拡張する方法について説明します。 属性は、型やフィールドなどのプログラミング要素に注釈を付けるための、キーワードに似た記述的な宣言です。
ms.date: 10/14/2020
helpviewer_keywords:
- metadata, extending
- attributes [.NET], metadata
- elements [.NET], attributes
- common language runtime, attributes
- annotating programming elements
- keyword-like descriptive declarations
- runtime, attributes
- extending metadata
ms.assetid: 30386922-1e00-4602-9ebf-526b271a8b87
ms.openlocfilehash: e41299b83ae451117ab6829eee928b0d2306be19
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829077"
---
# <a name="extend-metadata-using-attributes"></a>属性を使用したメタデータの拡張

共通言語ランタイムでは、属性と呼ばれるキーワードに似た記述的な宣言を追加して、型、フィールド、メソッド、プロパティなどのプログラミング要素に注釈を付けることができます。 ランタイム用にコードをコンパイルすると、コードは Microsoft Intermediate Language (MSIL) に変換され、コンパイラによって生成されるメタデータと共に、ポータブル実行可能 (PE) ファイルに格納されます。 属性を使用すると、ランタイム リフレクション サービスで抽出できる記述的な情報をメタデータに追加できます。 属性は、<xref:System.Attribute?displayProperty=nameWithType> から派生する特殊なクラスのインスタンスを宣言するときに、コンパイラによって作成されます。

.NET は、さまざまな理由で属性を使用し、多くの問題に対処します。 属性を使用して、データをシリアル化する方法を記述したり、セキュリティの適用に使用する特性を指定したりします。また、コードをデバッグしやすい状態に保つためにジャスト イン タイム (JIT) コンパイラによる最適化を制限する場合も、属性を使用します。 さらに、ファイル名やコードの作成者の記録、およびフォームの開発時にコントロールやメンバーを表示するかどうかの制御も、属性で指定します。

## <a name="related-articles"></a>関連記事

|Title|説明|
|-----------|-----------------|
|[属性の適用](applying-attributes.md)|コードの要素に属性を適用する方法を説明します。|
|[カスタム属性の記述](writing-custom-attributes.md)|カスタム属性クラスをデザインする方法を説明します。|
|[属性に格納されている情報の取得](retrieving-information-stored-in-attributes.md)|実行コンテキストに読み込まれるコードのカスタム属性を取得する方法を説明します。|
|[メタデータと自己言及的なコンポーネント](../metadata-and-self-describing-components.md)|メタデータの概要と、それが .NET のポータブル実行可能 (PE) ファイル内でどのように実装されるかについて説明します。|
|[方法:  リフレクションのみのコンテキストにアセンブリを読み込む](../../framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)」を参照してください。|リフレクションのみのコンテキストでカスタム属性情報を取得する方法を説明します。|

## <a name="reference"></a>関連項目

- <xref:System.Attribute?displayProperty=nameWithType>
