---
title: ガベージ コレクション ETW イベント
description: ガベージコレクション ETW イベントに関する詳細情報を表示します。 説明されているイベントには、GCStart_V1、GCEnd_V1、GCHeapStats_V1、GCCreateSegment_V1 などがあります。
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
ms.openlocfilehash: 58ad874ef6a12c18c404640aa66577c391573534
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309743"
---
# <a name="garbage-collection-etw-events"></a>ガベージ コレクション ETW イベント

これらのイベントは、ガベージ コレクションに関連する情報を収集します。 ガベージ コレクションが実行された回数、ガベージ コレクションの間に解放されたメモリの量など、診断やデバッグに役立つ情報を入手できます。

このカテゴリは、次のイベントで構成されます。

- [GCStart_V1 イベント](#gcstart_v1-event)
- [GCEnd_V1 イベント](#gcend_v1-event)
- [GCHeapStats_V1 イベント](#gcheapstats_v1-event)
- [GCCreateSegment_V1 イベント](#gccreatesegment_v1-event)
- [GCFreeSegment_V1 イベント](#gcfreesegment_v1-event)
- [GCRestartEEBegin_V1 イベント](#gcrestarteebegin_v1-event)
- [GCRestartEEEnd_V1 イベント](#gcrestarteeend_v1-event)
- [GCSuspendEE_V1 イベント](#gcsuspendee_v1-event)
- [GCSuspendEEEnd_V1 イベント](#gcsuspendeeend_v1-event)
- [GCAllocationTick_V2 イベント](#gcallocationtick_v2-event)
- [GCFinalizersBegin_V1 イベント](#gcfinalizersbegin_v1-event)
- [GCFinalizersEnd_V1 イベント](#gcfinalizersend_v1-event)
- [GCCreateConcurrentThread_V1 イベント](#gccreateconcurrentthread_v1-event)
- [GCTerminateConcurrentThread_V1 イベント](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a>GCStart_V1 イベント  

次の表に、キーワードとレベルを示します。 詳細については、「 [CLR ETW のキーワードとレベル](clr-etw-keywords-and-levels.md)」を参照してください。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|情報提供 (4)|

次の表に、イベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`GCStart_V1`|1|ガベージ コレクションが開始されました。|

次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|Count|win:UInt32|*n*回めのガベージ コレクション。|
|奥行き|win:UInt32|収集されるジェネレーション。|
|理由|win:UInt32|ガベージ コレクションが発生した理由:<br /><br /> 0x0 - 小さなオブジェクト ヒープの割り当て。<br /><br /> 0x1 - 強制実行。<br /><br /> 0x2 - メモリ不足。<br /><br /> 0x3 - 空。<br /><br /> 0x4 - 大きなオブジェクト ヒープの割り当て。<br /><br /> 0x5 - 領域不足 (小さなオブジェクト ヒープが対象)。<br /><br /> 0x6 - 領域不足 (大きなオブジェクト ヒープが対象)。<br /><br /> 0x7 - 強制実行されるが、ブロッキングとして強制されない。|
|Type|win:UInt32|0x0 - バックグラウンド ガベージ コレクションの外部で発生するブロッキング ガベージ コレクション。<br /><br /> 0x1 - バックグラウンド ガベージ コレクション。<br /><br /> 0x2 - バックグラウンド ガベージ コレクションの実行中に発生するブロッキング ガベージ コレクション。|
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="gcend_v1-event"></a>GCEnd_V1 イベント

次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|情報提供 (4)|

次の表に、イベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`GCEnd_V1`|2|ガベージ コレクションが終了しました。|

次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|Count|win:UInt32|*n*回めのガベージ コレクション。|
|奥行き|win:UInt32|収集されたジェネレーション。|
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="gcheapstats_v1-event"></a>GCHeapStats_V1 イベント

次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|情報提供 (4)|

次の表に、イベント情報を示します。

|Event|イベント ID|説明|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|4|各ガベージ コレクション終了時のヒープの統計情報を示します。|

次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|GenerationSize0|win:UInt64|ジェネレーション 0 メモリのサイズ (バイト単位)。|
|TotalPromotedSize0|win:UInt64|ジェネレーション 0 からジェネレーション 1 に移されたバイト数。|
|GenerationSize1|win:UInt64|ジェネレーション 1 メモリのサイズ (バイト単位)。|
|TotalPromotedSize1|win:UInt64|ジェネレーション 1 からジェネレーション 2 に移されたバイト数。|
|GenerationSize2|win:UInt64|ジェネレーション 2 メモリのサイズ (バイト単位)。|
|TotalPromotedSize2|win:UInt64|最後のガベージ コレクションの後にジェネレーション 2 に残ったバイト数。|
|GenerationSize3|win:UInt64|大きなオブジェクト ヒープのサイズ (バイト単位)。|
|TotalPromotedSize3|win:UInt64|最後のガベージ コレクションの後に大きなオブジェクト ヒープに残ったバイト数。|
|FinalizationPromotedSize|win:UInt64|終了準備が完了しているオブジェクトの合計サイズ (バイト単位)。|
|FinalizationPromotedCount|win:UInt64|終了準備が完了しているオブジェクトの数。|
|PinnedObjectCount|win:UInt32|ピン止めオブジェクト (移動できないオブジェクト) の数。|
|SinkBlockCount|win:UInt32|使用中の同期ブロックの数。|
|GCHandleCount|win:UInt32|使用中のガベージ コレクション ハンドルの数。|
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|
  
## <a name="gccreatesegment_v1-event"></a>GCCreateSegment_V1 イベント

次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|情報提供 (4)|

次の表に、イベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|5|新しいガベージ コレクション セグメントが作成されました。 既に実行されているプロセスでトレースを有効にした場合は、このイベントが各既存セグメントについて発生します。|

次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|Address|win:UInt64|セグメントのアドレス。|
|サイズ|win:UInt64|セグメントのサイズ。|
|Type|win:UInt32|0x0 - 小さなオブジェクト ヒープ。<br /><br /> 0x1 - 大きなオブジェクト ヒープ。<br /><br /> 0x2 - 読み取り専用ヒープ。|
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|

ガベージ コレクターによって割り当てられるセグメントのサイズは実装に固有であり、定期的な更新プログラムによる場合を含め、いつでも変更されることがあります。 アプリでは、セグメント サイズを推測することや、特定のセグメント サイズに依存することを絶対に避けてください。また、セグメントの割り当てに使用可能なメモリの量を構成しようとしてもなりません。

## <a name="gcfreesegment_v1-event"></a>GCFreeSegment_V1 イベント

次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|情報提供 (4)|

次の表に、イベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|6|ガベージ コレクション セグメントが解放されました。|

次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|Address|win:UInt64|セグメントのアドレス。|
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="gcrestarteebegin_v1-event"></a>GCRestartEEBegin_V1 イベント

次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|情報提供 (4)|

次の表に、イベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|7|共通言語ランタイムの中断からの再開が開始されました。|

イベント データはありません。

## <a name="gcrestarteeend_v1-event"></a>GCRestartEEEnd_V1 イベント

次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|情報提供 (4)|

次の表に、イベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|3|共通言語ランタイムの中断からの再開が終了しました。|

イベント データはありません。

## <a name="gcsuspendee_v1-event"></a>GCSuspendEE_V1 イベント

次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|情報提供 (4)|

次の表に、イベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|9|ガベージ コレクションのための実行エンジンの中断の開始。|

次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|原因|win:UInt16|0x0 - その他。<br /><br /> 0x1 - ガベージ コレクション。<br /><br /> 0x2 - アプリケーション ドメインのシャットダウン。<br /><br /> 0x3 - コード ピッチ。<br /><br /> 0x4 - シャットダウン。<br /><br /> 0x5 - デバッガー。<br /><br /> 0x6 - ガベージ コレクションの準備。|
|Count|win:UInt32|その時点の GC カウント。 通常、この後に後続の GC 開始イベントが表示され、そのカウントは、ガベージ コレクション中に、GC インデックスが増えるため、このカウント + 1 になります。|
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="gcsuspendeeend_v1-event"></a>GCSuspendEEEnd_V1 イベント

次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|情報提供 (4)|

次の表に、イベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|8|ガベージ コレクションのための実行エンジンの中断の終了。|

イベント データはありません。

## <a name="gcallocationtick_v2-event"></a>GCAllocationTick_V2 イベント

次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|情報提供 (4)|

次の表に、イベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|10|約 100 KB が割り当てられるたび。|

次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|AllocationAmount|win:UInt32|割り当てサイズ (バイト単位)。 この値は、ULONG (4,294,967,295 バイト) の長さより短い割り当ての場合に正確です。 割り当てがこれを超える場合、このフィールドには切り捨てられた値が含まれます。 非常に大きな割り当てには `AllocationAmount64` を使用します。|
|AllocationKind|win:UInt32|0x0 - 小さなオブジェクトの割り当て (小さなオブジェクト ヒープへの割り当て)。<br /><br /> 0x1 - 大きなオブジェクトの割り当て (大きなオブジェクト ヒープへの割り当て)。|
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|
|AllocationAmount64|win:UInt64|割り当てサイズ (バイト単位)。 この値は非常に大きな割り当ての場合に正確です。|
|TypeId|win:Pointer|MethodTable のアドレス。 このイベント中に複数の型のオブジェクトが割り当てられた場合、これは最後に割り当てられたオブジェクト (100 KB のしきい値を超えたオブジェクト) に対応する MethodTable のアドレスです。|
|TypeName|win:UnicodeString|割り当てられた型の名前。 このイベント中に複数の型のオブジェクトが割り当てられた場合は、これは最後に割り当てられたオブジェクト (100 KB のしきい値を超えたオブジェクト) の型です。|
|HeapIndex|win:UInt32|オブジェクトが割り当てられたヒープ。 ワークステーションのガベージ コレクションと共に実行する場合、この値は 0 (ゼロ) になります。|

## <a name="gcfinalizersbegin_v1-event"></a>GCFinalizersBegin_V1 イベント

次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|情報提供 (4)|

次の表に、イベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|14|ファイナライザーの実行の開始。|

イベント データはありません。

## <a name="gcfinalizersend_v1-event"></a>GCFinalizersEnd_V1 イベント

次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|情報提供 (4)|

次の表に、イベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|13|ファイナライザーの実行の終了。|

次の表に、イベント データを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|Count|win:UInt32|実行されたファイナライザーの数。|
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="gccreateconcurrentthread_v1-event"></a>GCCreateConcurrentThread_V1 イベント

次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|情報提供 (4)|
|`ThreadingKeyword` (0x10000)|情報提供 (4)|

次の表に、イベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|11|同時実行ガベージ コレクション スレッドが作成されました。|

イベント データはありません。

## <a name="gcterminateconcurrentthread_v1-event"></a>GCTerminateConcurrentThread_V1 イベント

次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|情報提供 (4)|
|`ThreadingKeyword` (0x10000)|情報提供 (4)|

次の表に、イベント情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|12|同時実行ガベージ コレクションスレッドが終了しました。|

イベント データはありません。

## <a name="see-also"></a>関連項目

- [CLR ETW イベント](clr-etw-events.md)
