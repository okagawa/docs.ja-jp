---
title: メソッドランタイムイベント
description: 「CLR メソッドイベント」、「clr メソッドマーカー」、「CLR メソッドの詳細イベント」、「MethodJittingStarted」など、メソッドに固有の診断情報を収集する .NET ランタイムイベントを参照してください。
ms.date: 11/13/2020
helpviewer_keywords:
- Method events (CoreCLR)
- ETW, EventPipe, LTTng method events (CoreCLR)
ms.openlocfilehash: f9d08efa420670cf7a8c863f115ff270998f2dca
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "96594042"
---
# <a name="net-runtime-method-events"></a>.NET ランタイムメソッドイベント

これらのイベントは、メソッド固有の情報を収集します。 これらのイベントのペイロードは、シンボルの解決に必要です。 また、これらのイベントは、読み込まれたメソッドやアンロードされたメソッドなどの有用な情報を提供します。 診断のためにこれらのイベントを使用する方法の詳細については、「 [.net アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)」を参照してください。

すべてのメソッド イベントのレベルは「情報提供 (4)」です。 すべてのメソッド詳細イベントのレベルは「詳細 (5)」です。

すべてのメソッド イベントは、ランタイム プロバイダーのもとでは `JITKeyword` (0x10) キーワードまたは `NGenKeyword` (0x20) キーワードが発生させ、ランダウン プロバイダーのもとでは `JitRundownKeyword` (0x10) または `NGENRundownKeyword` (0x20) が発生させます。

これらのイベントの V2 バージョンには ReJITID が含まれていますが、V1 バージョンではありません。

## <a name="methodload_v1-event"></a>MethodLoad_V1 イベント

次の表に、イベント情報を示します。

|event|イベント ID|説明|
|-----------|--------------|-----------------|
|`MethodLoad_V1`|141|メソッドが Just-In-Time 読み込み (JIT 読み込み) される時点、または NGEN イメージが読み込まれる時点で発生します。 動的メソッドとジェネリック メソッドは、メソッドの読み込みにこのバージョンを使用しません。 JIT ヘルパーがこのバージョンを使用することはありません。|

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) ランタイム プロバイダー|情報提供 (4)|
|`NGenKeyword` (0x20) ランタイム プロバイダー|情報提供 (4)|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|メソッドの一意の識別子。 JIT ヘルパー メソッドの場合、これはメソッドの開始アドレスに設定されます。|
|`ModuleID`|`win:UInt64`|このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。|
|`MethodStartAddress`|`win:UInt64`|メソッドの開始アドレス。|
|`MethodSize`|`win:UInt32`|メソッドのサイズ。|
|`MethodToken`|`win:UInt32`|動的メソッドおよび JIT ヘルパーの場合は 0。|
|`MethodFlags`|`win:UInt32`|0x1: 動的メソッド。<br /><br /> 0x2: ジェネリック メソッド。<br /><br /> 0x4: JIT コンパイル済みコード メソッド (それ以外の場合は NGEN ネイティブ イメージ コード)。<br /><br /> 0x8: ヘルパー メソッド。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="methodload_v2-event"></a>MethodLoad_V2 イベント

|event|イベント ID|説明|
|----------------|---------------|-----------------|
|`MethodLoad_V2`|141|メソッドが Just-In-Time 読み込み (JIT 読み込み) される時点、または NGEN イメージが読み込まれる時点で発生します。 動的メソッドとジェネリック メソッドは、メソッドの読み込みにこのバージョンを使用しません。 JIT ヘルパーがこのバージョンを使用することはありません。|

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) ランタイム プロバイダー|情報提供 (4)|
|`NGenKeyword` (0x20) ランタイム プロバイダー|情報提供 (4)|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|メソッドの一意の識別子。 JIT ヘルパー メソッドの場合、これはメソッドの開始アドレスに設定されます。|
|`ModuleID`|`win:UInt64`|このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。|
|`MethodStartAddress`|`win:UInt64`|メソッドの開始アドレス。|
|`MethodSize`|`win:UInt32`|メソッドのサイズ。|
|`MethodToken`|`win:UInt32`|動的メソッドおよび JIT ヘルパーの場合は 0。|
|`MethodFlags`|`win:UInt32`|0x1: 動的メソッド。<br /><br /> 0x2: ジェネリック メソッド。<br /><br /> 0x4: JIT コンパイル済みコード メソッド (それ以外の場合は NGEN ネイティブ イメージ コード)。<br /><br /> 0x8: ヘルパー メソッド。|
|`ReJITID`|`win:UInt64`|メソッドの ReJIT ID。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="methodunload_v1-event"></a>MethodUnLoad_V1 イベント

|event|イベント ID|説明|
|----------------|---------------|-----------------|
|`MethodUnLoad_V1`|142|モジュールがアンロードされるとき、またはアプリケーション ドメインが破棄されるときに発生します。 動的メソッドがメソッドのアンロードにこのバージョンを使用することはありません。|

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10)|情報提供 (4)|
|`NGenKeyword` 0x20|情報提供 (4)|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|メソッドの一意の識別子。 JIT ヘルパー メソッドの場合、これはメソッドの開始アドレスに設定されます。|
|`ModuleID`|`win:UInt64`|このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。|
|`MethodStartAddress`|`win:UInt64`|メソッドの開始アドレス。|
|`MethodSize`|`win:UInt32`|メソッドのサイズ。|
|`MethodToken`|`win:UInt32`|動的メソッドおよび JIT ヘルパーの場合は 0。|
|`MethodFlags`|`win:UInt32`|0x1: 動的メソッド。<br /><br /> 0x2: ジェネリック メソッド。<br /><br /> 0x4: JIT コンパイル済みコード メソッド (それ以外の場合は NGEN ネイティブ イメージ コード)。<br /><br /> 0x8: ヘルパー メソッド。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="methodunload_v2-event"></a>MethodUnLoad_V2 イベント

|event|イベント ID|説明|
|----------------|---------------|-----------------|
|`MethodUnLoad_V2`|142|モジュールがアンロードされるとき、またはアプリケーション ドメインが破棄されるときに発生します。 動的メソッドがメソッドのアンロードにこのバージョンを使用することはありません。|

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10)|情報提供 (4)|
|`NGenKeyword` 0x20|情報提供 (4)|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|メソッドの一意の識別子。 JIT ヘルパー メソッドの場合、これはメソッドの開始アドレスに設定されます。|
|`ModuleID`|`win:UInt64`|このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。|
|`MethodStartAddress`|`win:UInt64`|メソッドの開始アドレス。|
|`MethodSize`|`win:UInt32`|メソッドのサイズ。|
|`MethodToken`|`win:UInt32`|動的メソッドおよび JIT ヘルパーの場合は 0。|
|`MethodFlags`|`win:UInt32`|0x1: 動的メソッド。<br /><br /> 0x2: ジェネリック メソッド。<br /><br /> 0x4: JIT コンパイル済みコード メソッド (それ以外の場合は NGEN ネイティブ イメージ コード)。<br /><br /> 0x8: ヘルパー メソッド。|
|`ReJITID`|`win:UInt64`|メソッドの ReJIT ID。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="r2rgetentrypoint-event"></a>R2RGetEntryPoint イベント

|event|イベント ID|説明|
|----------------|---------------|-----------------|
|`R2RGetEntryPoint`|159|R2R エントリポイント参照が終了したときに発生します。|

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |情報提供 (4)|
|`NGenKeyword` 0x20 |情報提供 (4)|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|R2R メソッドの一意識別子。|
|`MethodNamespace`|`win:UnicodeString`|検索するメソッドの名前空間。|
|`MethodName`|`win:UnicodeString`|検索するメソッドの名前。|
|`MethodSignature`|`win:UnicodeString`|メソッドのシグネチャ (型名のコンマ区切りリスト)。|
|`EntryPoint`|`win:UInt64`|R2R メソッドのエントリポイントへのポインター|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="r2rgetentrypointstart-event"></a>R2RGetEntryPointStart イベント

|event|イベント ID|説明|
|----------------|---------------|-----------------|
|`R2RGetEntryPointStart`|160|R2R エントリポイント参照が開始されたときに発生します。|

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |情報提供 (4)|
|`NGenKeyword` 0x20 |情報提供 (4)|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|R2R メソッドの一意識別子。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="methodloadverbose_v1-event"></a>MethodLoadVerbose_V1 イベント

|event|イベント ID|説明|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|143|メソッドが JIT 読み込みされるとき、または NGEN イメージが読み込まれるときに発生します。 動的メソッドとジェネリック メソッドは、メソッドの読み込みに常にこのバージョンを使用します。 JIT ヘルパーは常にこのバージョンを使用します。|

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |情報提供 (4)|
|`NGenKeyword` 0x20 |情報提供 (4)|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|メソッドの一意の識別子。 JIT ヘルパー メソッドの場合は、メソッドの開始アドレスに設定されます。|
|`ModuleID`|`win:UInt64`|このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。|
|`MethodStartAddress`|`win:UInt64`|開始アドレス。|
|`MethodSize`|`win:UInt32`|メソッドの長さ。|
|`MethodToken`|`win:UInt32`|動的メソッドおよび JIT ヘルパーの場合は 0。|
|`MethodFlags`|`win:UInt32`|0x1: 動的メソッド。<br /><br /> 0x2: ジェネリック メソッド。<br /><br /> 0x4: JIT コンパイル済みメソッド (それ以外の場合は NGen.exe により生成)<br /><br /> 0x8: ヘルパー メソッド。|
|`MethodNameSpace`|`win:UnicodeString`|メソッドに関連付けられた完全な名前空間名。|
|`MethodName`|`win:UnicodeString`|メソッドに関連付けられた完全クラス名。|
|`MethodSignature`|`win:UnicodeString`|メソッドのシグネチャ (型名のコンマ区切りリスト)。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="methodloadverbose_v2-event"></a>MethodLoadVerbose_V2 イベント

|event|イベント ID|説明|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|143|メソッドが JIT 読み込みされるとき、または NGEN イメージが読み込まれるときに発生します。 動的メソッドとジェネリック メソッドは、メソッドの読み込みに常にこのバージョンを使用します。 JIT ヘルパーは常にこのバージョンを使用します。|

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |情報提供 (4)|
|`NGenKeyword` 0x20 |情報提供 (4)|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|メソッドの一意の識別子。 JIT ヘルパー メソッドの場合は、メソッドの開始アドレスに設定されます。|
|`ModuleID`|`win:UInt64`|このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。|
|`MethodStartAddress`|`win:UInt64`|開始アドレス。|
|`MethodSize`|`win:UInt32`|メソッドの長さ。|
|`MethodToken`|`win:UInt32`|動的メソッドおよび JIT ヘルパーの場合は 0。|
|`MethodFlags`|`win:UInt32`|0x1: 動的メソッド。<br /><br /> 0x2: ジェネリック メソッド。<br /><br /> 0x4: JIT コンパイル済みメソッド (それ以外の場合は NGen.exe により生成)<br /><br /> 0x8: ヘルパー メソッド。|
|`MethodNameSpace`|`win:UnicodeString`|メソッドに関連付けられた完全な名前空間名。|
|`MethodName`|`win:UnicodeString`|メソッドに関連付けられた完全クラス名。|
|`MethodSignature`|`win:UnicodeString`|メソッドのシグネチャ (型名のコンマ区切りリスト)。|
|`ReJITID`|`win:UInt64`|メソッドの ReJIT ID。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="methodunloadverbose_v1-event"></a>MethodUnLoadVerbose_V1 イベント

|event|イベント ID|説明|
|-----------|--------------|-----------------|
|`MethodUnLoadVerbose_V1`|144|動的メソッドが破棄されるとき、またはモジュールがアンロードされるとき、あるいはアプリケーション ドメインが破棄されるときに発生します。 動的メソッドは、メソッドのアンロードに常にこのバージョンを使用します。|

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |情報提供 (4)|
|`NGenKeyword` 0x20 |情報提供 (4)|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|メソッドの一意の識別子。 JIT ヘルパー メソッドの場合は、メソッドの開始アドレスに設定されます。|
|`ModuleID`|`win:UInt64`|このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。|
|`MethodStartAddress`|`win:UInt64`|開始アドレス。|
|`MethodSize`|`win:UInt32`|メソッドの長さ。|
|`MethodToken`|`win:UInt32`|動的メソッドおよび JIT ヘルパーの場合は 0。|
|`MethodFlags`|`win:UInt32`|0x1: 動的メソッド。<br /><br /> 0x2: ジェネリック メソッド。<br /><br /> 0x4: JIT コンパイル済みメソッド (それ以外の場合は NGen.exe により生成)<br /><br /> 0x8: ヘルパー メソッド。|
|`MethodNameSpace`|`win:UnicodeString`|メソッドに関連付けられた完全な名前空間名。|
|`MethodName`|`win:UnicodeString`|メソッドに関連付けられた完全クラス名。|
|`MethodSignature`|`win:UnicodeString`|メソッドのシグネチャ (型名のコンマ区切りリスト)。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="methodunloadverbose_v2-event"></a>MethodUnLoadVerbose_V2 イベント

|event|イベント ID|説明|
|-----------|--------------|-----------------|
|`MethodUnLoadVerbose_V2`|144|動的メソッドが破棄されるとき、またはモジュールがアンロードされるとき、あるいはアプリケーション ドメインが破棄されるときに発生します。 動的メソッドは、メソッドのアンロードに常にこのバージョンを使用します。|

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |情報提供 (4)|
|`NGenKeyword` 0x20 |情報提供 (4)|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|メソッドの一意の識別子。 JIT ヘルパー メソッドの場合は、メソッドの開始アドレスに設定されます。|
|`ModuleID`|`win:UInt64`|このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。|
|`MethodStartAddress`|`win:UInt64`|開始アドレス。|
|`MethodSize`|`win:UInt32`|メソッドの長さ。|
|`MethodToken`|`win:UInt32`|動的メソッドおよび JIT ヘルパーの場合は 0。|
|`MethodFlags`|`win:UInt32`|0x1: 動的メソッド。<br /><br /> 0x2: ジェネリック メソッド。<br /><br /> 0x4: JIT コンパイル済みメソッド (それ以外の場合は NGen.exe により生成)<br /><br /> 0x8: ヘルパー メソッド。|
|`MethodNameSpace`|`win:UnicodeString`|メソッドに関連付けられた完全な名前空間名。|
|`MethodName`|`win:UnicodeString`|メソッドに関連付けられた完全クラス名。|
|`MethodSignature`|`win:UnicodeString`|メソッドのシグネチャ (型名のコンマ区切りリスト)。|
|`ReJITID`|`win:UInt64`|メソッドの ReJIT ID。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="methodjittingstarted_v1-event"></a>MethodJittingStarted_V1 イベント

次の表に、キーワードとレベルを示します。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`JITKeyword` (0x10) |詳細 (5)|
|`NGenKeyword` 0x20 |詳細 (5)|

|event|イベント ID|説明|
|-----------|--------------|-----------------|
|`MethodJittingStarted_V1`|145|メソッドが JIT コンパイルされているときに発生します。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|メソッドの一意の識別子。|
|`ModuleID`|`win:UInt64`|このメソッドが属するモジュールの識別子。|
|`MethodToken`|`win:UInt32`|動的メソッドおよび JIT ヘルパーの場合は 0。|
|`MethodILSize`|`win:UInt32`|JIT コンパイルされるメソッドの共通中間言語 (CIL) のサイズ。|
|`MethodNameSpace`|`win:UnicodeString`|メソッドに関連付けられた完全クラス名。|
|`MethodName`|`win:UnicodeString`|メソッドの名前です。|
|`MethodSignature`|`win:UnicodeString`|メソッドのシグネチャ (型名のコンマ区切りリスト)。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="methodjitinliningsucceeded-event"></a>MethodJitInliningSucceeded イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`JITTracingKeyword` 0x1000 |詳細 (5)|

|event|イベント ID|説明|
|-----------|--------------|-----------------|
|`MethodJitInliningSucceeded`|185|JIT コンパイラによってメソッドが正常にインライン化された場合に発生します。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|コンパイルされるメソッドの名前空間。|
|`MethodBeingCompiledName`|`win:UnicodeString`|コンパイルされるメソッドの名前。|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|コンパイルされるメソッドのシグネチャ (型名のコンマ区切りリスト)。|
|`InlinerNamespace`|`win:UnicodeString`|このインライナ ("parent") メソッドの名前空間。|
|`InlinerName`|`win:UnicodeString`|このインライナ ("parent") メソッドの名前。|
|`InlinerNameSignature`|`win:UnicodeString`|このインライナ ("parent") メソッドのシグネチャ (型名のコンマ区切りリスト)。|
|`InlineeNamespace`|`win:UnicodeString`|インライン ("child") メソッドの名前空間。|
|`InlineeName`|`win:UnicodeString`|インライン ("child") メソッドの名前。|
|`InlineeNameSignature`|`win:UnicodeString`|インライン ("child") メソッドのシグネチャ (型名のコンマ区切りリスト)。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="methodjitinliningfailed-event"></a>MethodJitInliningFailed イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`JITTracingKeyword` 0x1000 |詳細 (5)|

|event|イベント ID|説明|
|-----------|--------------|-----------------|
|`MethodJitInliningFailed`|192|メソッドが JIT コンパイラによってインライン化されなかった場合に発生します。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|コンパイルされるメソッドの名前空間。|
|`MethodBeingCompiledName`|`win:UnicodeString`|コンパイルされるメソッドの名前。|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|コンパイルされるメソッドのシグネチャ (型名のコンマ区切りリスト)。|
|`InlinerNamespace`|`win:UnicodeString`|このインライナ ("parent") メソッドの名前空間。|
|`InlinerName`|`win:UnicodeString`|このインライナ ("parent") メソッドの名前。|
|`InlinerNameSignature`|`win:UnicodeString`|このインライナ ("parent") メソッドのシグネチャ (型名のコンマ区切りリスト)。|
|`InlineeNamespace`|`win:UnicodeString`|インライン ("child") メソッドの名前空間。|
|`InlineeName`|`win:UnicodeString`|インライン ("child") メソッドの名前。|
|`InlineeNameSignature`|`win:UnicodeString`|インライン ("child") メソッドのシグネチャ (型名のコンマ区切りリスト)。|
|`FailAlways`|`win:Boolean`|メソッドが not linable としてマークされているかどうか。|
|`FailReason`|`win:UnicodeString`|理由のインライン展開に失敗しました。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="methodjittailcallsucceeded-event"></a>MethodJitTailCallSucceeded イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`JITTracingKeyword` 0x1000 |詳細 (5)|

|event|イベント ID|説明|
|-----------|--------------|-----------------|
|`MethodJitTailCallSucceeded`|192|JIT コンパイラによって発生します。メソッドを正常に終了させることができます。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|コンパイルされるメソッドの名前空間。|
|`MethodBeingCompiledName`|`win:UnicodeString`|コンパイルされるメソッドの名前。|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|コンパイルされるメソッドのシグネチャ (型名のコンマ区切りリスト)。|
|`CallerNamespace`|`win:UnicodeString`|呼び出し元のメソッドの名前空間。|
|`CallerName`|`win:UnicodeString`|呼び出し元のメソッドの名前。|
|`CallerNameSignature`|`win:UnicodeString`|呼び出し元のメソッドのシグネチャ (型名のコンマ区切りのリスト)。|
|`CalleeNamespace`|`win:UnicodeString`|呼び出し先メソッドの名前空間。|
|`CalleeName`|`win:UnicodeString`|呼び出し先メソッドの名前。|
|`CalleeNameSignature`|`win:UnicodeString`|呼び出し先メソッドのシグネチャ (型名のコンマ区切りリスト)。|
|`TailPrefix`|`win:Boolean`|Tail プレフィックス命令であるかどうか。|
|`TailCallType`|`win:UInt32`|末尾呼び出しの種類。<br/><br/>0: tail 呼び出しを最適化します (エピローグ + jmp)<br/><br/>1: 再帰的な末尾呼び出し (メソッドの末尾の呼び出し自体)<br/><br/>2: ヘルパーによるテール呼び出し|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="methodjittailcallfailed-event"></a>MethodJitTailCallFailed イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`JITTracingKeyword` 0x1000 |詳細 (5)|

|event|イベント ID|説明|
|-----------|--------------|-----------------|
|`MethodJitTailCallFailed`|191|メソッドが末尾の呼び出しに失敗したときに JIT コンパイラによって発生します。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|コンパイルされるメソッドの名前空間。|
|`MethodBeingCompiledName`|`win:UnicodeString`|コンパイルされるメソッドの名前。|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|コンパイルされるメソッドのシグネチャ (型名のコンマ区切りリスト)。|
|`CallerNamespace`|`win:UnicodeString`|呼び出し元のメソッドの名前空間。|
|`CallerNam`e|`win:UnicodeString`|呼び出し元のメソッドの名前。|
|`CallerNameSignature`|`win:UnicodeString`|呼び出し元のメソッドのシグネチャ (型名のコンマ区切りのリスト)。|
|`CalleeNamespace`|`win:UnicodeString`|呼び出し先メソッドの名前空間。|
|`CalleeName`|`win:UnicodeString`|呼び出し先メソッドの名前。|
|`CalleeNameSignature`|`win:UnicodeString`|呼び出し先メソッドのシグネチャ (型名のコンマ区切りリスト)。|
|`TailPrefix`|`win:Boolean`|Tail プレフィックス命令であるかどうか。|
|`FailReason`|`win:UnicodeString`|理由の末尾の呼び出しが失敗しました。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="methodiltonativemap-event"></a>MethodILToNativeMap イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`JittedMethodILToNativeMapKeyword` 0x20000 |詳細 (5)|

|event|イベント ID|説明|
|----------------|---------------|-----------------|
|`MethodILToNativeMap`|190|JIT コンパイル済みメソッドの IL からネイティブへのマップイベントをマップします。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|メソッドの一意の識別子。|
|`ReJITID`|`win:UInt64`|メソッドの ReJIT ID。|
|`MethodExtent`|`win:UInt8`|Just-in-time メソッドの範囲。|
|`CountOfMapEntries`|`win:UInt8`|マップエントリの数|
|`ILOffsets`|`win:UInt32`|オフセット IL。|
|`NativeOffsets`|`win:UInt32`|ネイティブコードオフセット。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|
