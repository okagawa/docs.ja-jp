---
title: 型システムランタイムイベント
description: TypeLoadStart や Typeloadstart など、.NET 型システムに固有の診断情報を収集する .NET ランタイムイベントを参照してください。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- type system events (CoreCLR)
- ETW, EventPipe, LTTng type system events (CoreCLR)
ms.openlocfilehash: 8eee89cddb0098da2cb449a4be21945adac725e3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "96594037"
---
# <a name="net-runtime-type-events"></a>.NET ランタイム型イベント

これらのイベントは、型の読み込みに関する情報を収集します。 診断のためにこれらのイベントを使用する方法の詳細については、「 [.net アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)」を参照してください。

## <a name="typeloadstart-event"></a>TypeLoadStart イベント

|イベントを発生させるキーワード|event|Level|  
|-----------------------------------|-----------|-----------|  
|`TypeDiagnosticKeyword` 0x8000000000|情報提供 (4)|  

|event|イベント ID|説明|  
|-----------|--------------|-----------------|  
|`TypeLoadStart`|73|型の読み込みが開始されました。|

|フィールド名|データ型|説明|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|型の読み込み操作の ID。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|  

## <a name="typeloadstop-event"></a>TypeLoadStop イベント

|イベントを発生させるキーワード|Level|  
|-----------------------------------|-----------|-----------|  
|`TypeDiagnosticKeyword` 0x8000000000|情報提供 (4)|  

|event|イベント ID|説明|  
|-----------|--------------|-----------------|  
|`TypeLoadStop`|74|型の読み込みが完了しました。|

|フィールド名|データ型|説明|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|型の読み込み操作の ID (対応する TypeLoadStart イベントの TypeLoadStartID と一致します)。|
|`LoadLevel`|`win:UInt16`|「読み込みレベル」と入力します。|
|`TypeID`|`win:UInt64`|型ハンドルへのポインター。|
|`TypeName`|`win:UnicodeString`|型の名前。|
|`ClrInstanceID`|`win:UInt16`|CLR または CoreCLR のインスタンスの一意の ID。|  
