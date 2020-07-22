---
title: フレームワーク デザインのガイドライン
description: API の一貫性と使いやすさを確保するために、.NET を拡張して操作するライブラリを設計するためのフレームワークデザインガイドラインを参照してください。
titleSuffix: ''
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 17998adb1d18579f6763a80a82944e742e284e4e
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769068"
---
# <a name="framework-design-guidelines"></a>フレームワーク デザインのガイドライン
このセクションでは、.NET Framework を拡張および操作するライブラリを設計するためのガイドラインを示します。 この目標は、開発に使用されるプログラミング言語に依存しない統合プログラミングモデルを提供することで、ライブラリデザイナーが API の一貫性と使いやすさを保証できるようにすることです。 .NET Framework を拡張するクラスおよびコンポーネントを開発する場合は、これらのデザインガイドラインに従うことをお勧めします。 一貫性のないライブラリ設計は、開発者の生産性に悪影響を及ぼし、導入を推奨しません。  
  
 ガイドラインは、「」、「」、および「」という用語で構成される単純な推奨事項としてまとめられてい `Do` `Consider` `Avoid` `Do not` ます。 これらのガイドラインは、クラスライブラリデザイナーがさまざまなソリューション間のトレードオフを理解できるようにすることを目的としています。 優れたライブラリ設計では、これらの設計ガイドラインに違反することが必要になる場合があります。 このようなケースはまれであり、明確で説得力のある理由を決定することが重要です。  
  
 これらのガイドラインは、抜粋です*Framework の設計ガイドラインから、再利用可能な .Net ライブラリである2番目のエディション*(Krzysztof Cwalina と Brad abrams) の規則、表現、パターンについて説明しています。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [名前付けのガイドライン](naming-guidelines.md)  
 クラスライブラリのアセンブリ、名前空間、型、およびメンバーの名前付けに関するガイドラインを提供します。  
  
 [型デザインのガイドライン](type.md)  
 静的クラス、抽象クラス、インターフェイス、列挙体、構造体、およびその他の型を使用するためのガイドラインを提供します。  
  
 [メンバーデザインのガイドライン](member.md)  
 プロパティ、メソッド、コンストラクター、フィールド、イベント、演算子、およびパラメーターのデザインと使用に関するガイドラインを示します。  
  
 [機能拡張のデザイン](designing-for-extensibility.md)  
 サブクラス化、イベント、仮想メンバー、コールバックなどの拡張機能について説明し、フレームワークの要件に最も適したメカニズムを選択する方法について説明します。  
  
 [例外のデザインのガイドライン](exceptions.md)  
 例外をデザイン、スロー、キャッチするためのデザインガイドラインについて説明します。  
  
 [使用に関するガイドライン](usage-guidelines.md)  
 配列、属性、コレクションなどの共通型の使用、シリアル化のサポート、および等値演算子のオーバーロードに関するガイドラインについて説明します。  
  
 [一般的なデザインパターン](common-design-patterns.md)  
 依存関係プロパティの選択と実装に関するガイドラインを示します。  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [概要](../../framework/get-started/overview.md)
- [開発ガイド](../../framework/development-guide.md)
