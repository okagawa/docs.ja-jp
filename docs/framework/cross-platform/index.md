---
description: '詳細情報: .NET Framework を使用して複数のプラットフォームを開発する'
title: .NET Framework による複数のプラットフォームの開発
ms.date: 10/21/2020
ms.assetid: b153baaa-130c-4169-860b-e580591de91e
ms.openlocfilehash: 6223da53a4b2bf26e793ac01f31d9d1bfeb03f9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786480"
---
# <a name="develop-for-multiple-platforms-with-net-framework"></a>.NET Framework を使用して複数のプラットフォームを開発する

.NET Framework と Visual Studio を使用して、Microsoft と Microsoft 以外の両方のプラットフォームを対象としたアプリを開発できます。

[!INCLUDE [net-framework-future](../../../includes/net-framework-future.md)]

## <a name="options-for-cross-platform-development"></a>クロスプラットフォーム開発のオプション

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

複数プラットフォームを対象として開発する場合は、ソース コードやバイナリを共有し、.NET Framework コードと Windows ランタイム API の間で呼び出しを実行できます。

|目的|用途|
|-----------------------|------------|
|Windows Phone 8.1 アプリと Windows 8.1 アプリの間でソース コードを共有する|**共有プロジェクト** (Visual Studio 2013 更新プログラム 2 のユニバーサル アプリ テンプレート)。<br /><br /> -  Visual Basic は現在サポートされていません。<br />-  #`if` ステートメントを使用してプラットフォーム固有のコードを分離できます。<br /><br /> 詳細については、次の情報を参照してください。<br /><br /> -   [コーディングを開始する](/windows/uwp/get-started/create-uwp-apps)<br />-   [Visual Studio を使用したユニバーサル XAML アプリのビルド](https://devblogs.microsoft.com/visualstudio/using-visual-studio-to-build-universal-xaml-apps/) (ブログ記事)<br />-   [Visual Studio を使用した XAML 収束アプリの構築](https://channel9.msdn.com/Events/Build/2014/3-591) (ビデオ)|
|異なるプラットフォームを対象とするアプリ間でバイナリを共有する|プラットフォームに依存しないコードの **ポータブル クラス ライブラリ プロジェクト**。<br /><br /> -  この方法は通常、ビジネス ロジックを実装するコードに使用されます。<br />-  Visual Basic または C# を使用できます。<br />-  API のサポートはプラットフォームによって異なります。<br />-  Windows 8.1 および Windows Phone 8.1 を対象としたポータブル クラス ライブラリ プロジェクトでは、Windows ランタイム API と XAML がサポートされます。 これらの機能は、古いバージョンのポータブル クラス ライブラリでは使用できません。<br />-  必要に応じて、インターフェイスまたは抽象クラスを使用してプラットフォーム固有のコードを抽象化できます。<br /><br /> 詳細については、次の情報を参照してください。<br /><br /> -   [ポータブル クラス ライブラリ](portable-class-library.md)<br />-   [ポータブル クラス ライブラリの作成方法](/archive/blogs/dsplaisted/how-to-make-portable-class-libraries-work-for-you) (ブログ記事)<br />-   [MVVM を利用した汎用性のあるクラス ライブラリの使用](using-portable-class-library-with-model-view-view-model.md) <br />-   [複数のプラットフォームを対象とするライブラリのアプリ リソース](app-resources-for-libraries-that-target-multiple-platforms.md) <br />-   [.NET 移植性アナライザー](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) (Visual Studio 拡張機能)|
|Windows 8.1 および Windows Phone 8.1 以外のプラットフォームを対象としたアプリの間でソース コードを共有する|**[リンクとして追加]** 機能。<br /><br /> -  この方法は、両方のアプリに共通しているが、何らかの理由で移植できないアプリ ロジックに適しています。 この機能は Visual Basic または Visual C# のコードに使用できます。<br />     たとえば Windows Phone 8 と Windows 8 は Windows ランタイム API を共有しますが、ポータブル クラス ライブラリはこれらのプラットフォームでは Windows ランタイムをサポートしていません。 Windows Phone 8 アプリと、Windows 8 を対象とした Windows ストア アプリの間で共通する Windows ランタイム コードを共有するには、`Add as link` を使用できます。<br /><br /> 詳細については、次の情報を参照してください。<br /><br /> -   [[リンクとして追加] でコードを共有する](/previous-versions/windows/apps/jj714082(v=vs.105))<br />-   [方法: 既存の項目をプロジェクトに追加する](/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))|
|.NET Framework を使用して Windows ストア アプリを作成するか、または .NET Framework コードから Windows ランタイム API を呼び出します。|.NET Framework C# または Visual Basic コードの **Windows ランタイム API**。 .NET Framework を使用して Windows ストア アプリを作成します。 2 つのプラットフォーム間の API の違いについて注意してください。 ただし、これらの違いに対処するためのクラスがあります。<br /><br /> 詳細については、次の情報を参照してください。<br /><br /> -   [Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート](support-for-windows-store-apps-and-windows-runtime.md) <br />-   [Windows ランタイムへの URI の引き渡し](passing-a-uri-to-the-windows-runtime.md) <br />-   <xref:System.IO.WindowsRuntimeStreamExtensions><br />-    <xref:System.WindowsRuntimeSystemExtensions>|
|Microsoft 以外のプラットフォームに対応した .NET Framework アプリの開発|.NET Framework の **ポータブル クラス ライブラリの参照アセンブリ** と、Visual Studio 拡張機能またはサードパーティ ツール (Xamarin など)。<br /><br /> 詳細については、次の情報を参照してください。<br /><br /> -   [すべてのプラットフォームでポータブル クラス ライブラリが利用可能に](https://devblogs.microsoft.com/dotnet/portable-class-library-pcl-now-available-on-all-platforms/) (ブログの投稿)<br />-   [Xamarin ドキュメント](/xamarin)|
|JavaScript および HTML を使用したクロスプラットフォーム開発|Windows 8.1 と Windows Phone 8.1 の Windows ランタイム API に対する開発を行うための、Visual Studio 2013 更新プログラム 2 の **ユニバーサル アプリ テンプレート**。 現在、クロスプラットフォーム アプリを開発するときに .NET Framework API で JavaScript と HTML を使用することはできません。<br /><br /> 詳細については、次の情報を参照してください。<br /><br /> -   [JavaScript プロジェクト テンプレート](/previous-versions/windows/apps/hh758331(v=win.10))<br />-   [JavaScript を使用した Windows ランタイム アプリの Windows Phone への移植](/previous-versions/windows/apps/dn636144(v=win.10))|
