---
title: コンピューター リソースへのアクセス
ms.date: 07/20/2015
helpviewer_keywords:
- computer resources [Visual Basic]
- My.Computer object [Visual Basic], tasks
- computer resources [Visual Basic], accessing
ms.assetid: 75b81c88-f7c0-46e0-95c8-0c006d2120f9
ms.openlocfilehash: 9595abaa1daa2b4a4436577d58856183dcb4d9ac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401785"
---
# <a name="accessing-computer-resources-visual-basic"></a>コンピューター リソースへのアクセス (Visual Basic)

`My.Computer` オブジェクトは、`My` の中心となる 3 つのオブジェクトの 1 つであり、情報とよく使用される機能へのアクセスを提供します。 `My.Computer` には、アプリケーションが実行されているコンピューターにアクセスするためのメソッド、プロパティ、イベントが用意されています。 そのオブジェクトには、以下のものがあります。

- <xref:Microsoft.VisualBasic.Devices.Audio>
- クリップボード (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)
- <xref:Microsoft.VisualBasic.Devices.Clock>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>
- <xref:Microsoft.VisualBasic.Devices.Keyboard>
- <xref:Microsoft.VisualBasic.Devices.Mouse>
- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Ports>
- レジストリ (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)

## <a name="in-this-section"></a>このセクションの内容

[サウンドの再生](playing-sounds.md)  
`My.Computer.Audio` に関連付けられたタスクを一覧表示します (例: バックグラウンドでのサウンドの再生)。

[クリップボードのデータの格納と読み取り](storing-data-to-and-reading-from-the-clipboard.md)  
`My.Computer.Clipboard` に関連付けられたタスクを一覧表示します (例: クリップボードからのデータ読み取り、またはクリップボードへのデータ書き込み)。

[コンピューターについての情報の取得](getting-information-about-the-computer.md)  
`My.Computer.Info` に関連付けられたタスクを一覧表示します (例: コンピューターの完全な名前または IP アドレスの特定)。

[キーボードへのアクセス](accessing-the-keyboard.md)  
`My.Computer.Keyboard` に関連付けられたタスクを一覧表示します (例: CapsLock がオンになっているかどうかの特定)。

[マウスへのアクセス](accessing-the-mouse.md)  
`My.Computer.Mouse` に関連付けられたタスクを一覧表示します (例: マウスの有無の特定)。

[ネットワーク操作の実行](performing-network-operations.md)  
`My.Computer.Network` に関連付けられたタスクを一覧表示します (例: ファイルのアップロードまたはダウンロード)。

[コンピューターのポートへのアクセス](accessing-the-computer-s-ports.md)  
`My.Computer.Ports` に関連付けられたタスクを一覧表示します (例: 使用できるシリアル ポートの表示、またはシリアル ポートへの文字列の送信)。

[レジストリからの読み取りとレジストリへの書き込み](reading-from-and-writing-to-the-registry.md)  
`My.Computer.Registry` に関連付けられたタスクを一覧表示します (例: レジストリ キーからのデータ読み取り、またはレジストリ キーへのデータ書き込み)。
