---
title: 例外ランタイムイベント
description: 「例外と例外処理に固有の診断情報を収集する .NET ランタイムイベント」を参照してください。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- exception events (CoreCLR)
- exception handling events (CoreCLR)
- ETW, EventPipe, LTTng exception events (CoreCLR)
ms.openlocfilehash: f4f63c8469f9c734b872ddaec8d1d7f7f0427576
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96594103"
---
# <a name="net-runtime-exception-events"></a>.NET ランタイム例外イベント

これらのランタイムイベントは、スローされた例外に関する情報をキャプチャします。 診断のためにこれらのイベントを使用する方法の詳細については、「 [.net アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)」を参照してください。

## <a name="exceptionthrown_v1-event"></a>ExceptionThrown_V1 イベント

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|エラー (1)|

 次の表にイベント情報を示します。

|event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ExceptionThrown_V1`|80|マネージド例外がスローされます。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`ExceptionType`|`win:UnicodeString`|例外の種類 (`System.NullReferenceException` など)。|
|`ExceptionMessage`|`win:UnicodeString`|実際の例外メッセージ。|
|`EIPCodeThrow`|`win:Pointer`|例外が発生した命令ポインター。|
|`ExceptionHR`|`win:UInt32`|例外 [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a)。|
|`ExceptionFlags`|`win:UInt16`|`0x01`: HasInnerException。<br /><br /> `0x02`: IsNestedException.<br /><br /> `0x04`: IsRethrownException.<br /><br /> `0x08`: IsCorruptedStateException (プロセスの状態が破損していることを示します。「 [破損状態の例外の処理](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)」を参照してください)。<br /><br /> `0x10`: IsCLSCompliant (から派生した例外 <xref:System.Exception> は cls に準拠していますが、それ以外の場合は cls に準拠していません)。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="exceptioncatchstart-event"></a>ExceptionCatchStart イベント

このイベントは、マネージ例外の catch ハンドラーが開始されると生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|情報提供 (4)|

 次の表にイベント情報を示します。

|event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ExceptionCatchStart`|250|マネージ例外は、ランタイムによって処理されます。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|例外が発生した命令ポインター。|
|`MethodID`|`win:Pointer`|例外が発生したメソッドのメソッド記述子へのポインター。|
|`MethodName`|`win:UnicodeString`|例外が発生したメソッドの名前。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="exceptioncatchstop-event"></a>ExceptionCatchStop イベント

このイベントは、マネージ例外の catch ハンドラーが終了したときに生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|情報提供 (4)|

 次の表にイベント情報を示します。

|event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ExceptionCatchStop`|251|マネージ例外の catch ハンドラーが実行されます。|

## <a name="exceptionfinallystart-event"></a>Exceptionfinを開始するイベント

このイベントは、マネージ例外の finally ハンドラーが開始したときに生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|情報提供 (4)|

 次の表にイベント情報を示します。

|event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ExceptionFinallyStart`|252|マネージ例外は、ランタイムによって処理されます。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|例外が発生した命令ポインター。|
|`MethodID`|`win:Pointer`|例外が発生したメソッドのメソッド記述子へのポインター。|
|`MethodName`|`win:UnicodeString`|例外が発生したメソッドの名前。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|

## <a name="exceptionfinallystop-event"></a>Exceptionfinが停止イベント

このイベントは、マネージ例外の catch ハンドラーが終了したときに生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|情報提供 (4)|

 次の表にイベント情報を示します。

|event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ExceptionFinallyStop`|253|マネージ例外 finally ハンドラーが実行されます。|

## <a name="exceptionfilterstart-event"></a>ExceptionFilterStart イベント

このイベントは、マネージ例外のフィルター処理が開始されるときに生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|情報提供 (4)|

 次の表にイベント情報を示します。

|event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ExceptionFilterStart`|254|マネージ例外のフィルター処理が開始されます。|

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|例外が発生した命令ポインター。|
|`MethodID`|`win:Pointer`|例外が発生したメソッドのメソッド記述子へのポインター。|
|`MethodName`|`win:UnicodeString`|例外が発生したメソッドの名前。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR のインスタンスの一意の ID。|

## <a name="exceptionfilterstop-event"></a>ExceptionFilterStop イベント

このイベントは、マネージ例外のフィルター処理が終了したときに生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|情報提供 (4)|

 次の表にイベント情報を示します。

|event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ExceptionFilteringStart`|255|マネージ例外のフィルター処理が終了します。|

## <a name="exceptionthrownstop-event"></a>ExceptionThrownStop イベント

このイベントは、スローされたマネージ例外の処理がランタイムによって完了したときに生成されます。

|イベントを発生させるキーワード|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` (0x8000)|情報提供 (4)|
  
 次の表にイベント情報を示します。

|event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ExceptionThrownStop`|256|マネージ例外のフィルター処理が終了します。|
