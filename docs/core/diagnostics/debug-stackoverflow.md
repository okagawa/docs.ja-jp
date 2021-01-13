---
title: Debugging StackOverflow エラー
description: StackOverflow 例外の診断方法について説明します
ms.topic: tutorial
ms.date: 12/22/2020
ms.openlocfilehash: 92edf854ddcc2e778949d74eff1370cf27db25b4
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/24/2020
ms.locfileid: "97764930"
---
# <a name="debugging-stackoverflow-errors"></a>Debugging StackOverflow エラー

<xref:System.StackOverflowException> は、入れ子になったメソッド呼び出しが多くなりすぎ、実行スタックがオーバーフローした場合にスローされます。  

たとえば、次のようなアプリがあるとします。

````
using System;

namespace temp
{
    class Program
    {
        static void Main(string[] args)
        {
            Main(args); // oops this recursion won't stop
        }
    }
}
````

スタック領域がなくなるまで、Main メソッドによって継続的にそれ自体が呼び出されます。  スタック領域がなくなると、実行を継続できず、<xref:System.StackOverflowException> がスローされます。  

````
> dotnet run
Stack overflow.
````

> [!NOTE]
> .NET 5 以降では、呼び出し履歴がコンソールに出力されます。

> [!NOTE]
> この記事では、lldb でスタック オーバーフローをデバッグする方法について説明します。 Windows で実行している場合、[Visual Studio](/visualstudio/debugger/what-is-debugging) または [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging) でアプリをデバッグすることをお勧めします。  

## <a name="example"></a>例

1. クラッシュ時にダンプを収集するようにそれを構成した状態でアプリを実行します

    ````
    > export COMPlus_DbgEnableMiniDump=1
    > dotnet run
    Stack overflow.
    Writing minidump with heap to file /tmp/coredump.6412
    Written 58191872 bytes (14207 pages) to core file
    ````

2. [dotnet-sos](dotnet-sos.md) を使用して SOS 拡張機能をインストールします

    ````
    dotnet-sos install
    ````

3. lldb でダンプをデバッグし、失敗したスタックを確認します

    ````
    lldb --core /temp/coredump.6412
    (lldb) bt
    ...
        frame #261930: 0x00007f59b40900cc
        frame #261931: 0x00007f59b40900cc
        frame #261932: 0x00007f59b40900cc
        frame #261933: 0x00007f59b40900cc
        frame #261934: 0x00007f59b40900cc
        frame #261935: 0x00007f5a2d4a080f libcoreclr.so`CallDescrWorkerInternal at unixasmmacrosamd64.inc:867
        frame #261936: 0x00007f5a2d3cc4c3 libcoreclr.so`MethodDescCallSite::CallTargetWorker(unsigned long const*, unsigned long*, int) at callhelpers.cpp:70
        frame #261937: 0x00007f5a2d3cc468 libcoreclr.so`MethodDescCallSite::CallTargetWorker(this=<unavailable>, pArguments=0x00007ffe8222e7b0, pReturnValue=0x0000000000000000, cbReturnValue=0) at callhelpers.cpp:604
        frame #261938: 0x00007f5a2d4b6182 libcoreclr.so`RunMain(MethodDesc*, short, int*, PtrArray**) [inlined] MethodDescCallSite::Call(this=<unavailable>, pArguments=<unavailable>) at callhelpers.h:468
    ...
    ````

4. 一番上のフレーム `0x00007f59b40900cc` が数回繰り返されます。 [SOS](sos-debugging-extension.md) `ip2md` コマンドを使用し、`0x00007f59b40900cc` アドレスに配置されているメソッドを判別します

    ````
    (lldb) ip2md 0x00007f59b40900cc
    MethodDesc:   00007f59b413ffa8
    Method Name:          temp.Program.Main(System.String[])
    Class:                00007f59b4181d40
    MethodTable:          00007f59b4190020
    mdToken:              0000000006000001
    Module:               00007f59b413dbf8
    IsJitted:             yes
    Current CodeAddr:     00007f59b40900a0
    Version History:
      ILCodeVersion:      0000000000000000
      ReJIT ID:           0
      IL Addr:            0000000000000000
         CodeAddr:           00007f59b40900a0  (MinOptJitted)
         NativeCodeVersion:  0000000000000000
    Source file:  /temp/Program.cs @ 9
    ````

5. 示されたメソッド temp.Program.Main(System.String[]) とソース "/temp/Program.cs @ 9" を参照し、問題を突き止められるか確認します。 依然として不明の場合、コードのその領域でログ記録を追加できます。

## <a name="see-also"></a>参照

* [.NET でのダンプの概要](dumps.md)
* [Linux ダンプのデバッグ](debug-linux-dumps.md)
* [.NET 用 SOS デバッガー拡張](sos-debugging-extension.md)
