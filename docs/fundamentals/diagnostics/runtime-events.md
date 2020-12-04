---
title: ランタイムイベント
description: ETW、LTTng、または EventPipe で使用できる .NET ランタイム (CoreCLR) によって生成される診断イベントを確認します。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- runtime events (CoreCLR)
- ETW, EventPipe runtime events (CoreCLR)
ms.openlocfilehash: 33fa7275ce40934ce043b4d0dba5749c37515755
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "96594049"
---
# <a name="net-runtime-events"></a>.NET ランタイムイベント

.NET ランタイム (CoreCLR) は、、、などのさまざまなメカニズムを使用して使用できる .NET アプリケーションの問題を診断するために使用できるさまざまなイベントを生成し `ETW` `LTTng` `EventPipe` ます。

このドキュメントは、.NET Core ランタイムによって発生するイベントの参照として機能します。

.NET Framework のランタイムイベントについては、「 [CLR ETW events](../../framework/performance/clr-etw-events.md)」を参照してください。

## <a name="in-this-section"></a>このセクションの内容

[競合イベント](runtime-contention-events.md)\
これらのイベントは、モニターのロック競合に関する情報を収集します。

[ガベージコレクションイベント](runtime-garbage-collection-events.md)\
これらのイベントは、ガベージ コレクションに関連する情報を収集します。 ガベージコレクションが実行された回数、ガベージコレクション中に解放されたメモリの量など、診断やデバッグに役立ちます。

[例外イベント](runtime-exception-events.md)\
これらのランタイムイベントは、スローされた例外に関する情報をキャプチャします。

[相互運用イベント](runtime-interop-events.md)\
これらのランタイムイベントは、共通中間言語 (CIL) のスタブ生成に関する情報をキャプチャします。

[ローダーイベントとバインダーイベント](runtime-loader-binder-events.md)\
これらのイベントは、アセンブリとモジュールの読み込みとアンロードに関する情報を収集します。

[メソッドイベント](runtime-method-events.md)\
これらのイベントは、メソッド固有の情報を収集します。 これらのイベントのペイロードは、シンボルの解決に必要です。 さらに、これらのイベントは、メソッドが呼び出された回数などの有用な情報を提供します。

[スレッドイベント](runtime-thread-events.md)\
これらのイベントは、ワーカー スレッドと I/O スレッドに関する情報を収集します。

[型イベント](runtime-type-events.md)\
これらのイベントは、型システムに関する情報を収集します。
