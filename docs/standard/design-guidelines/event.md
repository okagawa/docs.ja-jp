---
description: '詳細情報: イベントのデザイン'
title: イベントのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: d64bfb13792aa9d646560de844acddd9b7e188c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642202"
---
# <a name="event-design"></a>イベントのデザイン

イベントは、最も一般的に使用されるコールバック (フレームワークからユーザー コードを呼び出すことができるようにするコンストラクト) の形式です。 他のコールバック メカニズムとしては、デリゲートを受け取るメンバー、仮想メンバー、インターフェイス ベースのプラグインがあります。使いやすさに関する調査のデータからは、開発者の大半が、他のコールバック メカニズムを使用するよりイベントの方が使いやすいと感じていることがわかります。 イベントは、Visual Studio や多くの言語と問題なく統合されます。

 イベントには 2 つのグループがあることに注意してください。つまり、システムの状態が変化する前に発生するイベント (プリイベントと呼ばれます) と、状態が変化した後で発生するイベント (ポストイベントと呼ばれます) です。 プリイベントの例である `Form.Closing` は、フォームが閉じられる前に発生します。 ポストイベントの例である `Form.Closed` は、フォームが閉じられた後で発生します。

 ✔️ イベントの場合は、"起動 (fire)" や "トリガー (trigger)" ではなく、"発生 (raise)" という用語を使用します。

 ✔️ イベント ハンドラーとして使用する新しいデリゲートを手動で作成するのではなく、<xref:System.EventHandler%601?displayProperty=nameWithType> を使用します。

 ✔️ イベント引数としては <xref:System.EventArgs> のサブクラスを使用することを検討します。ただし、イベントでイベント処理メソッドにデータを渡す必要がないことが確実であるときは例外で、その場合は `EventArgs` 型を直接使用できます。

 `EventArgs` を直接使用する API を出荷した場合、互換性を損なうことなく、イベントで渡されるデータを追加することはできません。 サブクラスを使用した場合は、最初は完全に空であっても、必要に応じてサブクラスにプロパティを追加できます。

 ✔️ 各イベントを発生させるには、保護された仮想メソッドを使用します。 これは、アンシールド クラスでの非静的イベントにのみ適用され、構造体、シールド クラス、または静的イベントには適用されません。

 メソッドの目的は、派生クラスでオーバーライドを使用してイベントを処理する方法を提供することです。 オーバーライドは、派生クラスで基底クラスのイベントを処理するための、より柔軟かつ高速で、いっそう自然な方法です。 慣例として、メソッドの名前は、"On" で始まり、その後にイベントの名前を付けたものにする必要があります。

 派生クラスでは、オーバーライドの中でメソッドの基底の実装を呼び出さないことを選択できます。 そのためには、基底クラスが正常に動作するために必要な処理をメソッドに含めないでください。

 ✔️ イベントを発生させる保護されたメソッドに 1 つのパラメーターを渡します。

 パラメーターには `e` という名前を付け、イベント引数クラスとして型指定する必要があります。

 ❌ 非静的イベントを発生させるときは、センダーとして null を渡さないでください。

 ✔️ 静的イベントを発生させるときは、センダーとして null を渡します。

 ❌ イベントを発生させるときは、イベント データ パラメーターとして null を渡さないでください。

 イベント処理メソッドにデータを何も渡したくない場合は、`EventArgs.Empty` を渡す必要があります。 開発者は、このパラメーターは null ではないものと想定しています。

 ✔️ エンド ユーザーがキャンセルできるイベントを発生させることを検討します。 これはプリイベントにのみ適用されます。

 エンド ユーザーがイベントをキャンセルできるようにするには、<xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> またはそのサブクラスをイベント引数として使用します。

### <a name="custom-event-handler-design"></a>カスタム イベント ハンドラーの設計

 ジェネリックがサポートされていなかった古いバージョンの CLR をフレームワークで使用する必要がある場合など、`EventHandler<T>` を使用できない場合があります。 そのような場合は、カスタム イベント ハンドラーのデリゲートの設計と開発が必要になることがあります。

 ✔️ イベント ハンドラーの戻り値の型には void を使用します。

 イベント ハンドラーでは、複数のイベント処理メソッドを、場合によっては複数のオブジェクトで、呼び出すことができます。 イベント処理メソッドで値を返すことが許可された場合、イベントの呼び出しごとに複数の戻り値が返されます。

 ✔️ イベント ハンドラーの 1 番目のパラメーターは、型として `object` を使用し、名前を `sender` にします。

 ✔️ イベント ハンドラーの 2 番目のパラメーターは、型として <xref:System.EventArgs?displayProperty=nameWithType> またはそのサブクラスを使用し、名前を `e` にします。

 ❌ イベント ハンドラーで 3 つ以上のパラメーターを使用することはできません。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [メンバーのデザインのガイドライン](member.md)
- [フレームワーク デザインのガイドライン](index.md)
