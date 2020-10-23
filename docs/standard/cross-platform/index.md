---
title: .NET Framework を使用した複数のプラットフォーム向けの開発
ms.date: 10/21/2020
ms.technology: dotnet-standard
ms.assetid: b153baaa-130c-4169-860b-e580591de91e
ms.openlocfilehash: 75c33d2d2eb4bda0bcd86e19c5098af4a63863e9
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471965"
---
# <a name="develop-for-multiple-platforms-with-net-framework"></a>.NET Framework による複数のプラットフォーム向けの開発

.NET Framework と Visual Studio を使用して、Microsoft と Microsoft 以外の両方のプラットフォーム用のアプリを開発できます。

[!INCLUDE [net-framework-future](../../../includes/net-framework-future.md)]

## <a name="options-for-cross-platform-development"></a>クロスプラットフォーム開発のオプション

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

複数プラットフォームを対象として開発する場合は、ソース コードやバイナリを共有し、.NET Framework コードと Windows ランタイム API の間で呼び出しを実行できます。

|目的|用途|
|-----------------------|------------|
|Windows Phone 8.1 アプリと Windows 8.1 アプリの間でソース コードを共有する|**共有プロジェクト** (Visual Studio 2013、Update 2 のユニバーサルアプリテンプレート)。<br /><br /> -現在 Visual Basic はサポートしていません。<br />-# ステートメントを使用して、プラットフォーム固有のコードを分離することができ `if` ます。<br /><br /> 詳細については、次の情報を参照してください。<br /><br /> -   [コーディングを開始する](/windows/uwp/get-started/create-uwp-apps)<br />-   [Visual Studio を使用したユニバーサル XAML アプリの構築](https://devblogs.microsoft.com/visualstudio/using-visual-studio-to-build-universal-xaml-apps/) (ブログの投稿)<br />-   [Visual Studio を使用した XAML 収束アプリの構築](https://channel9.msdn.com/Events/Build/2014/3-591) (ビデオ)|
|異なるプラットフォームを対象とするアプリ間でバイナリを共有する|プラットフォームに依存しないコードの**ポータブルクラスライブラリプロジェクト**。<br /><br /> -この方法は、通常、ビジネスロジックを実装するコードに使用されます。<br />-Visual Basic または C# を使用できます。<br />-API のサポートはプラットフォームによって異なります。<br />-Windows 8.1 を対象とするポータブルクラスライブラリプロジェクトと Windows Phone 8.1 サポート Windows ランタイム Api および XAML。 これらの機能は、古いバージョンのポータブル クラス ライブラリでは使用できません。<br />-必要に応じて、インターフェイスまたは抽象クラスを使用して、プラットフォーム固有のコードを抽象化できます。<br /><br /> 詳細については、次の情報を参照してください。<br /><br /> -   [ポータブルクラスライブラリ](cross-platform-development-with-the-portable-class-library.md)<br />-   [ポータブルクラスライブラリを機能](/archive/blogs/dsplaisted/how-to-make-portable-class-libraries-work-for-you) させる方法 (ブログの投稿)<br />-   [MVVM でのポータブルクラスライブラリの使用](using-portable-class-library-with-model-view-view-model.md) <br />-   [複数のプラットフォームを対象とするライブラリのアプリリソース](app-resources-for-libraries-that-target-multiple-platforms.md) <br />-   [.Net 移植性アナライザー](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) (Visual Studio 拡張機能)|
|Windows 8.1 および Windows Phone 8.1 以外のプラットフォームを対象としたアプリの間でソース コードを共有する|**リンクとして追加** 機能。<br /><br /> -この方法は、何らかの理由で、両方のアプリに共通のアプリロジックに適していますが、移植できません。 この機能は Visual Basic または Visual C# のコードに使用できます。<br />     たとえば Windows Phone 8 と Windows 8 は Windows ランタイム API を共有しますが、ポータブル クラス ライブラリはこれらのプラットフォームでは Windows ランタイムをサポートしていません。 Windows Phone 8 アプリと、Windows 8 を対象とした Windows ストア アプリの間で共通する Windows ランタイム コードを共有するには、`Add as link` を使用できます。<br /><br /> 詳細については、次の情報を参照してください。<br /><br /> -   [[リンクとして追加してコードを共有する。](/previous-versions/windows/apps/jj714082(v=vs.105))<br />-   [方法: プロジェクトに既存の項目を追加する](/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))|
|.NET Framework を使用して Windows ストア アプリを作成するか、または .NET Framework コードから Windows ランタイム API を呼び出します。|.NET Framework C# または Visual Basic コードから**api を Windows ランタイム**し、.NET Framework を使用して Windows ストアアプリを作成します。 2 つのプラットフォーム間の API の違いについて注意してください。 ただし、これらの違いに対処するためのクラスがあります。<br /><br /> 詳細については、次の情報を参照してください。<br /><br /> -   [Windows ストアアプリと Windows ランタイムの .NET Framework サポート](support-for-windows-store-apps-and-windows-runtime.md) <br />-   [URI を Windows ランタイムに渡す](passing-a-uri-to-the-windows-runtime.md) <br />-   <xref:System.IO.WindowsRuntimeStreamExtensions><br />-    <xref:System.WindowsRuntimeSystemExtensions>|
|Microsoft 以外のプラットフォームに対応した .NET Framework アプリの開発|.NET Framework の**ポータブルクラスライブラリ参照アセンブリ**と、Visual Studio 拡張機能または Xamarin などのサードパーティツール。<br /><br /> 詳細については、次の情報を参照してください。<br /><br /> -   [すべてのプラットフォームでポータブルクラスライブラリを使用できるようになりました。](https://devblogs.microsoft.com/dotnet/portable-class-library-pcl-now-available-on-all-platforms/) (ブログの投稿)<br />-   [Xamarin のドキュメント](/xamarin)|
|JavaScript および HTML を使用したクロスプラットフォーム開発|Visual Studio 2013、Update 2 の**ユニバーサルアプリテンプレート**は、Windows 8.1 および Windows Phone 8.1 の Windows ランタイム api に対して開発します。 現時点では、.NET Framework Api で JavaScript と HTML を使用して、クロスプラットフォームアプリを開発することはできません。<br /><br /> 詳細については、次の情報を参照してください。<br /><br /> -   [JavaScript プロジェクトテンプレート](/previous-versions/windows/apps/hh758331(v=win.10))<br />-   [JavaScript を使用した Windows ランタイムアプリの Windows Phone への移植](/previous-versions/windows/apps/dn636144(v=win.10))|
