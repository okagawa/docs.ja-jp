---
title: Firefox に対応した WPF プラグインがインストールされているかどうかを確認する
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: 91680859c1742e5d5443d626c81273a80504f4a8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740404"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>方法: Firefox に対応した WPF プラグインがインストールされているかどうかを確認する

Firefox 用の Windows Presentation Foundation (WPF) プラグインを使用すると、XAML ブラウザー アプリケーション (XBAP) と Loose XAML ファイルを Mozilla Firefox ブラウザーで実行できます。 このトピックでは、Firefox 用 WPF プラグインがインストールされているかどうかを確認するために管理者が使用できる HTML と JavaScript で記述されたスクリプトを提供します。

> [!NOTE]
> .NET Framework のインストール、配置、検出については、「[開発者向けの .NET Framework のインストール](../../install/guide-for-developers.md)」をご覧ください。

## <a name="example"></a>例

.NET Framework 3.5 がインストールされている場合、クライアント コンピューターには Firefox 用の WPF プラグインが構成されます。 次のスクリプトの例では、Firefox 用の WPF プラグインを確認し、適切なステータス メッセージを表示します。

```html
<HTML>

  <HEAD>
    <TITLE>Test for the WPF plug-in for Firefox</TITLE>
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />
    <SCRIPT type="text/javascript">
    <!--
    function OnLoad()
    {

       // Check for the WPF plug-in for Firefox and report
       var msg = "The WPF plug-in for Firefox is ";
       var wpfPlugin = navigator.plugins["Windows Presentation Foundation"];
       if( wpfPlugin != null ) {
          document.writeln(msg + " installed.");
       }
       else {
          document.writeln(msg + " not installed. Please install or reinstall the .NET Framework 3.5.");
       }
    }
    -->
    </SCRIPT>
  </HEAD>

  <BODY onload="OnLoad()" />

</HTML>
```

Firefox 用 WPF プラグインの確認が成功すると、次のステータス メッセージが表示されます。

`The WPF plug-in for Firefox is installed.`

それ以外の場合は、次のステータス メッセージが表示されます。

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a>関連項目

- [.NET Framework 3.0 がインストールされているかどうかを確認する](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [.NET Framework 3.5 がインストールされているかどうかを確認する](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [WPF XAML ブラウザー アプリケーションの概要](wpf-xaml-browser-applications-overview.md)
