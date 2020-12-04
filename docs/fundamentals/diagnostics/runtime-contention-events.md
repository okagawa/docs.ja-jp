---
title: ロック競合ランタイムイベントの監視
description: モニターのロック競合に固有の情報を収集する ETW イベントを参照してください。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- monitor lock contention events (CoreCLR)
- ETW, EventPipe, LTTng contention events (CoreCLR)
ms.openlocfilehash: 38e5f493d4b223b4839dbd6f814cf656722189b2
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "96594054"
---
# <a name="net-runtime-contention-events"></a>.NET ランタイム競合イベント

これらのランタイムイベント `Monitor.Enter` は、または C# の lock キーワードを使用したなど、モニターのロックの競合に関する情報をキャプチャします。 診断のためにこれらのイベントを使用する方法の詳細については、「 [.net アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)」を参照してください。

## <a name="contentionstart_v1-event"></a>ContentionStart_V1 イベント

このイベントは、モニターのロック競合の開始時に生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ContentionKeyword` (0x4000)|情報提供 (4)|

 次の表にイベント情報を示します。

|event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|81|モニターのロックの競合が開始されます。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|`0` マネージドの場合 `1` ネイティブの場合。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="contentionstop_v1-event"></a>ContentionStop_V1 イベント

このイベントは、モニターロックの競合が終了したときに生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ContentionKeyword` (0x4000)|情報提供 (4)|

 次の表にイベント情報を示します。

|event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ContentionStop_V1`|91|モニターのロックの競合が終了します。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|`0` マネージドの場合 `1` ネイティブの場合。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|
|`DurationNs`|`win:Double`|競合の継続時間 (ナノ秒単位)。|
