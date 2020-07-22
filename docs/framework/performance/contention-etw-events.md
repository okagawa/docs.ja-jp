---
title: 競合 ETW イベント-.NET
description: 競合 ETW イベントの詳細を取得します。これは、ランタイムによって使用される、システムのスレッドのロックまたはネイティブロックの競合が発生した場合に発生します。
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: a36b091e0896562fffdb66e895d70049ce0667d7
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309600"
---
# <a name="contention-etw-events"></a>競合 ETW イベント

競合イベントは、ランタイムによって使用される <xref:System.Threading.Monitor?displayProperty=nameWithType> ロックまたはネイティブ ロックの競合が発生するたびに発生します。 競合は、あるスレッドが、別のスレッドが保持しているロックを待機しているときに発生します。

競合イベントが発生するキーワードとイベントのレベルを次の表に示します  詳細については、「 [CLR ETW のキーワードとレベル](clr-etw-keywords-and-levels.md)」を参照してください。

|イベントを発生させるキーワード|レベル|
|-----------------------------------|-----------|
|`ContentionKeyword` (0x4000)|情報提供 (4)|

次の表に、イベントに関する情報を示します。

|Event|イベント ID|いつ発生するか|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|81|競合が開始されたとき。 このイベントには、スレッドがロックの取得を待機する前のスピン時間は含まれません。このイベントが発生するのは、スレッドがロックの取得を待機するときだけです。|
|`ContentionStop`|91|競合が終了したとき。|

次の表に、イベントデータを示します。

|フィールド名|データ型|説明|
|----------------|---------------|-----------------|
|Flags|win:UInt8|マネージドの場合は 0、ネイティブの場合は 1 です。|
|ClrInstanceID|win:UInt16|CLR のインスタンスの一意の ID。|

## <a name="see-also"></a>関連項目

- [CLR ETW イベント](clr-etw-events.md)
