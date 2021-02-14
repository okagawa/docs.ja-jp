---
description: '詳細情報: イベントとコールバック'
title: イベントとコールバック
ms.date: 10/22/2008
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
ms.openlocfilehash: 8a9049808ec0f7a490889ab1f17c4d8b8e8bd2b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642150"
---
# <a name="events-and-callbacks"></a>イベントとコールバック

コールバックは、フレームワークで、デリゲートを通じてユーザー コードにコールバックできるようにする拡張ポイントです。 これらのデリゲートは、通常、メソッドのパラメーターを通してフレームワークに渡されます。

 イベントはコールバックの特殊なケースであり、デリゲート (イベント ハンドラー) を提供する便利な一貫性のある構文をサポートしています。 さらに、イベントベースの API の使用では、Visual Studio のステートメント入力候補とデザイナーが役立ちます。 (「[イベントの設計](event.md)」を参照してください)。

 ✔️ コールバックを使用して、ユーザーがフレームワークによって実行されるカスタム コードを指定できるようにすることを検討してください。

 ✔️ イベントを使用して、ユーザーがオブジェクト指向設計を理解していなくてもフレームワークの動作をカスタマイズできるようにすることを検討してください。

 ✔️ 幅広い開発者が慣れていることと、Visual Studio のステートメント入力候補と統合されているため、単純なコールバックよりもイベントを優先してください。

 ❌ パフォーマンスを重視する API でコールバックを使用することは避けてください。

 ✔️ コールバックを使用して API を定義するときは、カスタム デリゲートではなく、新しい `Func<...>`、`Action<...>`、または `Expression<...>` 型を使用してください。

 `Func<...>` と `Action<...>` は、汎用デリゲートを表します。 `Expression<...>` は、コンパイルして実行時に呼び出すことができる関数定義を表していますが、シリアル化してリモート プロセスに渡すこともできます。

 ✔️ `Func<...>` と `Action<...>` デリゲートの使用に代わる `Expression<...>` の使用によるパフォーマンスへの影響を測定して理解してください。

 `Expression<...>` 型は、ほとんどの場合、`Func<...>` と `Action<...>` デリゲートと論理的に等価です。 これらの主な違いは、デリゲートはローカル プロセス シナリオで使用されることを意図しており、式は、リモート プロセスまたはコンピューターで式を評価することが有益であり、それが可能であるケースを対象としていることです。

 ✔️ デリゲートを呼び出すことは任意のコードを実行することであり、セキュリティ、正確性、および互換性に影響を与える可能性があることを理解しておいてください。

 *Portions &copy; 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [機能拡張のデザイン](designing-for-extensibility.md)
- [フレームワーク デザインのガイドライン](index.md)
