---
title: -platform
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: a6226b73d5d5d4d48a71afe39e8a546019d4c0bc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352342"
---
# <a name="-platform-visual-basic"></a>-platform (Visual Basic)
出力ファイルをどのプラットフォーム用の共通言語ランタイム (CLR) で実行するかを指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`x86`|32 ビット x86 互換 CLR で実行されるように、アセンブリをコンパイルします。|  
|`x64`|AMD64 または EM64T 命令セットをサポートするコンピューター上の 64 ビット CLR で実行されるように、アセンブリをコンパイルします。|  
|`Itanium`|Itanium プロセッサ搭載のコンピューター上の 64 ビット CLR で実行されるように、アセンブリをコンパイルします。|  
|`arm`|ARM (アドバンスト RISC マシン) プロセッサ搭載のコンピューター上で実行されるように、アセンブリをコンパイルします。|  
|`anycpu`|任意のプラットフォーム上で実行されるように、アセンブリをコンパイルします。 アプリケーションは、Windows の 32 ビット バージョンでは 32 ビット アプリケーションとして、Windows の 64 ビット バージョンでは 64 ビット アプリケーションとして実行されます。 このフラグが既定値です。|  
|`anycpu32bitpreferred`|任意のプラットフォーム上で実行されるように、アセンブリをコンパイルします。 アプリケーションは、Windows の 32 ビット バージョンおよび 64 ビット バージョンの両方で、 32 ビット アプリケーションとして実行されます。 このフラグは、実行可能ファイル (.EXE) に対してのみ有効であり、.NET Framework 4.5 が必要です。|  
  
## <a name="remarks"></a>Remarks  
 出力ファイルの対象となるプロセッサの種類を指定するには、`-platform` オプションを使用します。  
  
 通常、Visual Basic で記述された .NET Framework アセンブリは、プラットフォームに関係なく、同じように実行されます。 ただし、プラットフォーム間で動作が異なる場合があります。 その一般的な例を次に示します。  
  
- プラットフォームによってメンバーのサイズが変わる構造体 (ポインター型など)  
  
- 定数のサイズを含むポインター演算  
  
- ハンドルに `Integer` ではなく <xref:System.IntPtr> を使用した不適切なプラットフォーム呼び出しまたは COM 宣言  
  
- <xref:System.IntPtr> の `Integer` へのキャスト  
  
- すべてのプラットフォームに存在するとは限らないコンポーネントを使用したプラットフォーム呼び出しまたは COM 相互運用機能の使用  
  
 コードの実行対象となるアーキテクチャをあらかじめ想定している場合は、 **-platform** オプションを使用することで、いくつかの問題が軽減されます。 具体的には、次のように使用します。  
  
- 64 ビット プラットフォームを対象にし、アプリケーションを 32 ビット マシンで実行した場合、エラー メッセージは、このスイッチを使用しない場合よりも、エラー メッセージがかなり早期に出力され、より絞り込まれた内容になります。  
  
- オプションに `x86` フラグを設定し、その後、アプリケーションを 64 ビット マシンで実行した場合、アプリケーションはネイティブに実行されず、WOW サブシステムで実行されます。  
  
 64 ビット Windows オペレーティング システムの場合:  
  
- `-platform:x86` でコンパイルされたアセンブリは、WOW64 の下で動作する 32 ビット CLR で実行されます。  
  
- `-platform:anycpu` でコンパイルされた実行可能ファイルは、64 ビット CLR で実行されます。  
  
- `-platform:anycpu` でコンパイルでされた DLL は、ロード先のプロセスと同じ CLR で実行されます。  
  
- `-platform:anycpu32bitpreferred` でコンパイルされた実行可能ファイルは、32 ビット CLR で実行されます。  
  
 64 ビット バージョンの Windows で実行するアプリケーションを開発する方法の詳細については、「[64 ビット アプリケーション](../../../framework/64-bit-apps.md)」を参照してください。  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a>Visual Studio IDE で -platform を設定するには  
  
1. **ソリューション エクスプローラー**で、プロジェクトを選択し、 **[プロジェクト]** メニューを開いてから、 **[プロパティ]** をクリックします。  
  
2. **[コンパイル]** タブで、 **[32 ビットを優先]** チェック ボックスをオンまたはオフにするか、 **[対象の CPU]** 一覧で値を選択します。  
  
     詳細については、「[[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)」を参照してください。  
  
## <a name="example"></a>例  
 次の例は、`-platform` コンパイラ オプションを使用する方法を示しています。  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a>関連項目

- [-target (Visual Basic)](target.md)
- [Visual Basic のコマンド ライン コンパイラ](index.md)
- [コンパイル コマンド ラインのサンプル](sample-compilation-command-lines.md)
