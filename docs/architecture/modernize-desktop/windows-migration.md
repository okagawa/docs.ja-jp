---
title: Windows 10 の移行
description: パッケージ化や XAML アイランドなどの Windows 10 の機能の詳細について説明します。
ms.date: 12/29/2020
ms.openlocfilehash: 139a8f2354803dafeb0178b4dbfb57a95c4ddb34
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615946"
---
# <a name="windows-10-migration"></a>Windows 10 の移行

次のような状況が考えられます。 Windows 7 日以内に開発された動作中のデスクトップアプリケーションがあるとします。 その時点で利用可能な WPF テクノロジを使用しており、問題なく動作しますが、Windows 10 で実行したときの UI と動作が古くなっています。 これは、マトリックスなどの futuristic 映画を視聴し、Nokia 8110 デバイスを使用して Neo を表示する場合と似ています。 フィルムは20年後にうまく機能しますが、デバイスの最新化によるメリットが得られます。

Windows 10 のリリースでは、タブレットやタッチデバイスのようなシナリオをサポートする多くのイノベーションが導入され、Microsoft オペレーティングシステムのユーザーに最適なエクスペリエンスを提供しています。 たとえば、次のように操作できます。

- Windows Hello を使用して顔でサインインします。
- ペンを使用して、自動的に認識され、digitalized されるテキストを描画または手書き入力します。
- WinML を使用して、クラウド上に構築されたローカルでカスタマイズされた AI モデルを実行します。

これらのすべての機能は、Windows ランタイム (WinRT) ライブラリを通じて Windows 開発者に対して有効になっています。 これらの機能は、既存のデスクトップアプリで利用できます。これは、ライブラリが .NET Framework と .NET の両方にも公開されているためです。 XAML アイランドを使用して UI を最新化し、時間に従ってアプリのビジュアルと動作を向上させることもできます。

ここで注意すべき重要な点の1つは、この近代化パスに従うために .NET Framework テクノロジを破棄する必要がないことです。 .NET に移行しなくても、Windows 10 のすべての利点を活用して、その機能を維持することができます。 そのため、最新化パスを選択するための能力と柔軟性が得られます。

## <a name="winrt-apis"></a>WinRT Api

WinRT Api は、オブジェクト指向の適切に構造化されたアプリケーションプログラミングインターフェイス (Api) です。これにより、Windows 10 開発者は、オペレーティングシステムが提供するすべての機能にアクセスできるようになります。 WinRT Api を使用して、プッシュ通知、デバイス Api、Microsoft Ink、WinML などの機能をデスクトップアプリに統合できます。

一般に、WinRT Api は従来のデスクトップアプリから呼び出すことができます。 ただし、次の2つの主な領域には、この規則の例外があります。

* パッケージ id を必要とする Api。
* XAML やコンポジションなどの視覚化を必要とする Api。

### <a name="universal-windows-platform-uwp-packages"></a>ユニバーサル Windows プラットフォーム (UWP) パッケージ

#### <a name="application-package-identity"></a>アプリケーションパッケージ Id

UWP アプリには、OS がアプリケーションのインストールとアンインストールを管理する展開システムがあります。 この場合、インストールは宣言型である必要があります。つまり、インストール中にユーザーコードは実行されません。 その代わりに、アプリがシステムと統合する必要があるすべてのもの (プロトコル、ファイルの種類、拡張機能など) は、アプリケーションマニフェストで宣言されます。 配置時には、配置パイプラインによって統合ポイントが構成されます。 OS がすべての機能を管理し、それを追跡する唯一の方法は、"パッケージ" ごとに、アプリケーションの一意の識別子である id を持つことです。

一部の WinRT Api では、このパッケージ id が想定どおりに動作する必要があります。 ただし、ネイティブ C++ や .NET アプリなどの従来のデスクトップアプリでは、パッケージ id を必要としない異なる展開システムを使用します。 これらの WinRT Api をデスクトップアプリケーションで使用する場合は、パッケージ id を提供する必要があります。

続行する1つの方法は、追加のパッケージプロジェクトをビルドすることです。 パッケージプロジェクト内で、元のソースコードプロジェクトをポイントし、提供する Id 情報を指定します。 パッケージをインストールし、インストールされているアプリを実行すると、Id を必要とするすべての WinRT Api をコードで呼び出すことができるように自動的に識別されます。

```xml
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10">
    <Identity Name="YOUR-APP-GUID "
              Publisher="CN=YOUR COMPANY"
              Version="1.x.x.x" />
</Package>
```

API を含む型が [DualApiPartition](xref:Windows.Foundation.Metadata.DualApiPartitionAttribute) 属性でマークされているかどうかを調べることによって、パッケージ化されたアプリケーション id を必要とする api を確認できます。 そうであれば、従来のデスクトップアプリからの場合はを呼び出すことができます。 それ以外の場合は、パッケージプロジェクトのヘルプを使用して、クラシックデスクトップアプリを UWP に変換する必要があります。

<https://docs.microsoft.com/windows/desktop/apiindex/uwp-apis-callable-from-a-classic-desktop-app>

#### <a name="benefits-of-packaging"></a>パッケージ化の利点

これらの Api へのアクセスを提供するだけでなく、次のようなデスクトップアプリケーション用の Windows アプリパッケージを作成することによって、いくつかの利点を得ることができます。

* **展開の合理化**。 アプリには、ユーザーが信頼性の高い方法でアプリケーションをインストールして更新できるようにするための、優れた展開エクスペリエンスがあります。 ユーザーがアプリをアンインストールすることを選択した場合、そのアプリは完全に削除され、Windows の問題を回避するためのトレースは残されていません。

* **自動更新とライセンス**。 アプリケーションは、Microsoft Store の組み込みのライセンスと自動更新機能に参加できます。 自動更新機能は、ファイルの変更された部分だけがダウンロードされるため、非常に信頼性が高く効率的なメカニズムです。

* **リーチの拡大とシンプルな決済**。 そうではないかもしれませんが、Microsoft Store にアプリケーションを配布することを選択した場合は、何百万もの Windows 10 ユーザーに届きます。

* **UWP 機能の追加**。 UWP 機能は、自分のペースでアプリのパッケージに追加できます。

#### <a name="prepare-for-packaging"></a>パッケージ化の準備

デスクトップアプリケーションのパッケージ化に進む前に、プロセスを開始する前に対処する必要があるポイントがいくつかあります。 アプリケーションは、Microsoft Store の規則とポリシーを尊重し、UWP アプリケーションモデルで実行する必要があります。 たとえば、4.6.2 以降の .NET Framework で実行し、レジストリハイブに書き込む必要があり `HKEY_CURRENT_USER` ます。また、AppData フォルダーはユーザー固有のアプリローカルの場所に仮想化されます。

パッケージ化の設計目標は、他のアプリとの互換性を維持しながら、アプリケーションの状態をシステム状態から分離することです。 Windows 10 では、アプリケーションを UWP パッケージ内に配置することによって、この目標を達成しています。 実行時にファイルシステムとレジストリにいくつかの変更を検出してリダイレクトすることで、パッケージ化によって提供されるアプリケーションの信頼されたクリーンインストールとアンインストールの動作が保証されます。

デスクトップアプリケーション用に作成したパッケージは、デスクトップのみの完全に信頼されたアプリケーションであり、およびへの書き込み用にアプリに適用される軽量の仮想化があり `HKCU` `AppData` ます。 この仮想化により、従来のデスクトップアプリケーションと同じように、他のアプリと対話することができます。

##### <a name="installation"></a>インストール

アプリパッケージは *% ProgramFiles% \\ windowsapps \\ package_name* にインストールされます。実行可能ファイルはという名前 `app_name.exe` です。 各パッケージフォルダーには、パッケージ `AppxManifest.xml` アプリの特別な XML 名前空間を含むという名前のマニフェストが含まれています。 マニフェスト ファイル内の `<EntryPoint>` 要素で、完全信頼アプリを参照します。 アプリケーションが起動されると、アプリコンテナー内で実行されるのではなく、通常どおりユーザーとして実行されます。

展開後、パッケージ ファイルは読み取り専用としてマークされ、オペレーティング システムによって厳重にロックダウンされます。 これらのファイルが改ざんされると、Windows によりアプリの起動が回避されます。

##### <a name="file-system"></a>ファイル システム

OS は、フォルダーの場所に応じて、パッケージデスクトップアプリケーションに対してさまざまなレベルのファイルシステム操作をサポートします。

ユーザーの *AppData* フォルダーにアクセスしようとすると、システムによって、ユーザーごと、アプリごとのプライベートな場所がバックグラウンドで作成されます。 これにより、実際にプライベートコピーを変更しているときに、パッケージ化されたアプリケーションが実際の *AppData* を編集していると錯覚します。 このように書き込みのリダイレクトを行うことで、アプリによって行われたすべてのファイル変更をシステムで追跡できます。 その後、システム "rot" を削除し、ユーザーのアプリケーションの削除エクスペリエンスを向上させるために、これらのファイルをすべてクリーンアップできます。

##### <a name="registry"></a>レジストリ

アプリケーションパッケージには、実際のレジストリのと同等のものとして機能する、レジストリの .dat ファイルが含まれています。 `HKLM\Software` 実行時には、この仮想レジストリのハイブの内容がネイティブ システム ハイブにマージされ、両方が一括して表示されます。

すべての書き込みはパッケージのアップグレード中に保持され、アプリケーションがアンインストールされると削除されます。

##### <a name="uninstallation"></a>アンインストール

ユーザーがパッケージをアンインストールすると、の下にあるすべてのファイルとフォルダー `C:\Program Files\WindowsApps\package_name` が削除されます。また、AppData またはプロセス中にキャプチャされたレジストリへのリダイレクトされた書き込みもすべて削除されます。

パッケージ化されたアプリケーションがインストール、ファイルアクセス、レジストリ、およびアンインストールを処理する方法の詳細については、「」を参照してください <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-behind-the-scenes> 。

確認する項目の完全な一覧を取得でき <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-prepare> ます。

## <a name="how-to-add-winrt-apis-to-your-desktop-project"></a>デスクトッププロジェクトに WinRT Api を追加する方法

このセクションでは、既存の WPF アプリケーションでトースト通知を統合する方法に関するチュートリアルを紹介します。 コードの観点からは単純ですが、プロセス全体を示すのに役立ちます。 通知は、.NET アプリで使用できる多数の利用可能な WinRT Api の1つです。 この場合、API にはパッケージ Id が必要です。 Api でパッケージ Id が不要な場合、このプロセスはより簡単です。

ファイルを読み取り、その内容を画面に表示する既存の WPF サンプルアプリを見てみましょう。 目標は、アプリケーションの起動時にトースト通知を表示することです。

![サンプルアプリケーションを実行しているスクリーンショット](./media/windows-migration/sample-application.png)

最初に、使用する Windows 10 API にパッケージ Id が必要かどうかについて、次のリンクをチェックインする必要があります。

<https://docs.microsoft.com/windows/apps/desktop/modernize/desktop-to-uwp-supported-api>

このサンプルでは、 <xref:Windows.UI.Notifications.Notification?displayProperty=nameWithType> パッケージ化された id を必要とする API を使用します。

![Microsoft ドキュメントの Notification クラス](./media/windows-migration/notification-class-documentation.png)

WinRT API にアクセスするには、NuGet パッケージへの参照を追加 `Microsoft.Windows.SDK.Contracts` します。このパッケージは、バックグラウンドでマジックを実行します (詳細については、「」を参照してください <https://blogs.windows.com/windowsdeveloper/2019/04/30/calling-windows-10-apis-from-a-desktop-application-just-got-easier/> )。

これで、コードの追加を開始する準備が整いました。

`ShowToastNotification`アプリケーションの起動時に呼び出されるメソッドを作成します。 XML パターンからトースト通知を構築するだけです。

```csharp
private void ShowNotification(string title, string content, string image)
{
    string xmlString = $@"<toast><visual><binding template = 'ToastGeneric'><text>{title}</text><text>{content}</text><image src=>'{image}'</image></binding></visual></toast>";
    XmlDocument toastXml = new XmlDocument();
    toastXml.LoadXml(xmlString);
    ToastNotification toast = new ToastNotification(toastXml);
    ToastNotificationManager.CreateToastNotifier().Show(toast);
}
```

プロジェクトがビルドされますが、通知 API にはパッケージ Id が必要であり、提供されていないため、エラーが発生します。 Windows パッケージングプロジェクトをソリューションに追加すると、問題が解決されます。

![Visual Studio の [新しいプロジェクトの追加] ダイアログのスクリーンショット](./media/windows-migration/add-packaging-project.png)

サポートする Windows の最小バージョンとターゲットとするバージョンを選択します。 すべての WinRT Api がすべての Windows 10 バージョンでサポートされているわけではありません。 Windows 10 の更新プログラムごとに、このバージョンでのみ使用できる新しい Api が追加されます。下位レベルのサポートは使用できません。

![Windows の最小バージョンの選択](./media/windows-migration/select-versions.png)

次の手順では、プロジェクト参照を追加して WPF アプリケーションを Windows パッケージプロジェクトに追加します。

![Windows パッケージプロジェクトへの WPF アプリケーションの追加](./media/windows-migration/add-application.png)

![参照マネージャー](./media/windows-migration/reference-manager.png)

Windows パッケージプロジェクトでは、いくつかのアプリをパッケージ化できるため、エントリポイントを設定する必要があります。

![エントリポイントの設定](./media/windows-migration/set-entry-point.png)

次の手順では、ソリューション構成で WPF プロジェクトをスタートアッププロジェクトとして設定します。 F5 キーを押すと、コンパイルしてビルドし、結果を確認できます。

![実行中のサンプルアプリケーションと結果の表示](./media/windows-migration/sample-app-result.png)

アプリをインストールできるようにパッケージを生成してみましょう。 ストアの [   >  **アプリパッケージの作成**] を右クリックします。

![アプリパッケージの作成ダイアログ](./media/windows-migration/create-app-packages.png)

サイドローディングオプションを選択して、コンピューターからアプリを展開します。

![サイドローディングオプションの選択](./media/windows-migration/select-sideloading-option.png)

アプリのアプリケーションアーキテクチャを選択します。

![アプリケーションアーキテクチャの選択](./media/windows-migration/select-app-architecture.png)

最後に、[ **作成**] をクリックしてパッケージを作成します。

## <a name="xaml-islands"></a>XAML Islands

XAML アイランドは、Windows デスクトップ開発者が既存の Win32 アプリケーション (Windows フォームや WPF など) で UWP XAML コントロールを使用できるようにする一連のコンポーネントです。

![XAML アイランドの構造](./media/windows-migration/xaml-islands.png)

Win32 アプリには、標準のコントロールと、最新の世界のコントロールを含む UWP UI の "アイランド" を使用してイメージを作成できます。 概念は、のコンテンツを表示する web ページ内に iFrame がある場合と似ています。 `different page.`

Windows 10 Api から機能を追加するだけでなく、XAML アイランドを使用してアプリ内に UWP XAML の部分を追加できます。

Windows 10 1903 update では、Win32 ウィンドウで UWP XAML コンテンツをホストできるようにする一連の Api が導入されています。 XAML アイランドを使用できるのは、Windows 10 1903 で実行されているアプリのみです。

### <a name="the-road-to-xaml-islands"></a>XAML アイランドへの道路

XAML アイランドへの道路は、Microsoft が Win32 アプリ (Windows フォーム、WPF、およびネイティブの Win32 アプリ) を最新化するためのフレームワークとして WinRT Api を導入したときに、2012で開始されました。 ただし、WinRT 内の新しい UI コントロールは、新しいアプリケーションでは使用できましたが、既存のアプリケーションでは使用できませんでした。

2015では、Windows 10 と共に UWP が生まれました。 UWP を使用すると、XBox、Mobile、Desktop などの Windows デバイス間で動作するアプリを作成できます。 1年後、Microsoft はデスクトップブリッジ (旧称 Project Centennial) を発表しました。 デスクトップブリッジは、開発者が既存の Win32 アプリを Microsoft Store に持ち込むことを可能にする一連のツールです。 より多くの機能が2017に追加されたため、開発者は、アクションセンターでのライブタイルや通知など、新しい Windows 10 Api を活用して Win32 アプリを強化できます。 でも、新しい UI コントロールはありません。

ビルド2018では、開発者が新しい Windows 10 XAML コントロールを現在の Win32 アプリに使用する方法を発表しました。アプリを UWP に完全に移行する必要はありません。 UWP XAML アイランドとしてブランド化されていました。

### <a name="how-it-works"></a>しくみ

Windows 10 1903 更新プログラムでは、いくつかの XAML ホスティング Api が導入されています。 そのうちの2つは `WindowsXamlManager` 、と `DesktopWindowXamlSource` です。

クラスは、 `WindowsXamlManager` UWP XAML フレームワークを処理します。 この `InitializeForCurrentThread` メソッドは、Win32 アプリの現在のスレッド内の UWP XAML フレームワークを読み込みます。

`DesktopWindowXamlSource`は、XAML アイランドコンテンツのインスタンスです。 このプロパティには、を `Content` インスタンス化して設定するためのプロパティがあります。 は、 `DesktopWindowXamlSource` HWND からの入力をレンダリングして取得します。 XAML アイランドのどの HWND がアタッチされるかを把握しておく必要があります。また、親の HWND のサイズと位置を決定します。

WPF や Windows フォーム開発者は、通常は HWND をコード内に処理しないので、HWND ポインターや、Win32 および UWP ワールドを通信するための基になる配線について理解し、処理するのは困難な場合があります。

#### <a name="the-xaml-islands-net-wrappers"></a>XAML アイランド .NET ラッパー

Windows Community Toolkit には、xaml アイランドを簡単に使用できるようにする WPF または Windows フォーム用の XAML アイランド .NET ラッパーが用意されています。 これらのラッパーは、Hwnd、フォーカス管理などを管理します。 Windows フォーム WPF 開発者は、これらのラッパーを使用する必要があります。

Windows Community Toolkit には、ラップされたコントロールとホストコントロールの2種類のコントロールが用意されています。

##### <a name="wrapped-controls"></a>ラップされたコントロール

これらのラップされたコントロールは、いくつかの UWP コントロールを Windows フォームまたは WPF コントロールにラップし、開発者の UWP の概念を非表示にします。 これらのコントロールは次のとおりです。

* WebView と WebViewCompatible
* System.windows.controls.inkcanvas> と InkToolbar
* MediaPlayerElement
* MapControl

パッケージを `Microsoft.Toolkit.Wpf.UI.Controls` プロジェクトに追加し、名前空間への参照を含め、使用を開始します。

```xml
<Window
        ...
        xmlns:uwpControls="clr-namespace:Microsoft.Toolkit.Wpf.UI.Controls;assembly=Microsoft.Toolkit.Wpf.UI.Controls">
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="\*"/>
    </Grid.RowDefinitions>
    <uwpControls:InkToolbar TargetInkCanvas="{x:Reference Name=inkCanvas}"/>
    <uwpControls:InkCanvas Grid.Row="1" x:Name="inkCanvas" />
</Grid>
```

##### <a name="hosting-controls"></a>ホスト (コントロールを)

XAML アイランドの機能は、ほとんどのファーストパーティ製のコントロール、サードパーティのコントロール、および UWP 用に開発されたカスタムコントロールに拡張され、完全に機能する UI を備えた "アイランド" として Windows フォームおよび WPF に統合できます。 `WindowsXamlHost`WPF と Windows フォームのコントロールを使用すると、この操作を行うことができます。

たとえば、WPF でコントロールを使用するには、 `WindowsXamlHost` `Microsoft.Toolkit.Wpf.UI.XamlHost` Windows Community Toolkit によって提供されるパッケージへの参照を追加します。

を `WindowsXamlHost` UI コードに配置したら、読み込む UWP の種類を指定します。 `Button`カスタム UWP コントロールである複数の異なるコントロールによって構成される、、またはより複雑なコントロールを使用するように選択できます。

次の例は、UWP を追加する方法を示してい `Button` ます。

```xml
<Window
        ...
        xmlns:xamlhost="clr-namespace:Microsoft.Toolkit.Wpf.UI.XamlHost;assembly=Microsoft.Toolkit.Wpf.UI.XamlHost">

<xamlhost:WindowsXamlHost x:Name="myUwpButton"
                          InitialTypeName="Windows.UI.Xaml.Controls.Button" />
```

これにアプローチする方法について明確な推奨事項があります。また、1つのコントロールに複数のアイランドを持たせるよりも、カスタム複合コントロールを含む1つの大きな XAML アイランドを使用することをお勧めします。

XAML のコア機能の1つはバインドであり、Win32 コードと島の間で機能します。 そのため、たとえば、UWP と共に Win32 をバインドでき `Textbox` `Textbox` ます。 考慮すべき重要な点の1つとして、これらのバインディングは UWP から Win32 までの一方向のバインディングであるため、XAML アイランド内でを更新すると、 `Textbox` Win32 のテキストボックスが更新されますが、その他の方法は更新されません。

XAML アイランドの使用方法に関するチュートリアルについては、次を参照してください。

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-standard-control-with-xaml-islands>

#### <a name="adding-uwp-xaml-custom-controls"></a>UWP XAML カスタムコントロールの追加

XAML カスタムコントロールは、ユーザーまたはサードパーティ (WinUI 2.x コントロールを含む) によって作成されたコントロール (またはユーザーコントロール) です。 Windows フォームまたは WPF アプリでカスタム UWP コントロールをホストするには、次のものが必要です。

- `WindowsXamlHost`.Net アプリで UWP コントロールを使用する場合。
- オブジェクトを定義する UWP アプリプロジェクトを作成するには `XamlApplication`

WPF または Windows フォームプロジェクトは、 `Microsoft.Toolkit.Win32.UI.XamlHost.XamlApplication` Windows Community Toolkit によって提供されるクラスのインスタンスにアクセスできる必要があります。 このオブジェクトは、アプリケーションの現在のディレクトリにあるアセンブリ内のカスタム UWP XAML 型のメタデータを読み込むためのルートメタデータプロバイダーとして機能します。 これを行うには、WPF または Windows フォームプロジェクトと同じソリューションに空のアプリ (ユニバーサル Windows) プロジェクトを追加し、このプロジェクトの既定のアプリクラスを変更します。

カスタム UWP XAML コントロールは、この UWP アプリまたは WPF または Windows フォームプロジェクトと同じソリューションで参照する独立した UWP クラスライブラリプロジェクトに含めることができます。

詳細な手順については、「」をご覧ください。

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

#### <a name="the-windows-ui-library-winui-2"></a>Windows UI ライブラリ (WinUI 2)

OS に付属する受信トレイの Windows 10 コントロール以外にも、同じ UWP XAML チームが Windows UI ライブラリ (**WinUI 2**) で追加のコントロールを提供します。 WinUI 2 は、Windows UWP アプリ用のネイティブな Microsoft UI コントロールおよび機能を提供します。これらのコントロールは、XAML アイランドの内部で使用できます。

WinUI 2 はオープンソースであり、に関する情報を見つけることができ <https://github.com/microsoft/microsoft-ui-xaml> ます。

次の記事では、WinUI 2 ライブラリから UWP XAML コントロールをホストする方法について説明します。 <https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

### <a name="do-you-need-xaml-islands"></a>XAML アイランドが必要です

XAML アイランドは、アプリを完全に書き換えずに新しい UWP コントロールと動作を利用することで、ユーザーエクスペリエンスを向上させる既存の Win32 アプリを対象としています。 [Windows 10 api](/windows/uwp/porting/desktop-to-uwp-enhance)は既に利用できますが、XAML アイランドまでは UI に関連しない api のみを利用できます。

新しい Windows アプリを開発している場合は、 [UWP アプリ](/windows/uwp/get-started/universal-application-platform-guide) が適切な方法であると思います。

### <a name="the-road-ahead-xaml-islands-winui-30"></a>先行する XAML アイランド: WinUI 3.0

Windows 8 以降では、windows UI プラットフォーム (XAML UI フレームワーク、ビジュアルコンポジションレイヤー、入力処理など) が Windows の不可欠な部分として出荷されています。 これは、UI テクノロジの最新の機能強化を活用するために、最新バージョンの UI にアップグレードする必要があることを意味します。これにより、アプリの開発時にイノベーションの速度が低下します。 この2つの進化サイクルを分離し、イノベーションを促進するために、Microsoft は、WinUI プロジェクトに積極的に取り組んでいます。

2018年2月2日以降、Microsoft は、UWP SDK に基づいて構築された別の NuGet パッケージとして、いくつかの新しい XAML UI コントロールと機能の配布を開始しました。

![WinUI 2.0 の構造](./media/windows-migration/winui2.png)

WinUI 3 は、アクティブな開発中であり、WinUI の範囲を大幅に拡大して、UWP SDK から完全に分離される完全な UI プラットフォームを追加します。

![WinUI 3.0 の構造](./media/windows-migration/winui3.png)

XAML フレームワークは、GitHub で開発され、 [NuGet](/nuget/what-is-nuget) パッケージとして帯域外で出荷されるようになりました。

OS の一部として同梱されている既存の UWP XAML API に対して、新しい機能更新プログラムが提供されることはなくなります。 Windows 10 のサポートライフサイクルに従って、セキュリティ更新プログラムと重要な修正プログラムが引き続き提供されます。

ユニバーサル Windows プラットフォームには、XAML フレームワークだけでなく (アプリケーションとセキュリティモデル、メディアパイプライン、Xbox と Windows 10 シェルの統合、広範なデバイスのサポート) が含まれており、進化し続ける予定です。 新しい XAML 機能はすべて、代わりに WinUI の一部として開発および出荷されます。

#### <a name="winui-3-in-desktop-app-and-winui-xaml-islands"></a>デスクトップアプリと WinUI XAML アイランドの WinUI 3

ご覧のように、WinUI 3 は UWP XAML の進化であり、UWP アプリモデルとすべての要件 (MSIX パッケージ ID、サンドボックス、CoreWindow など) で自然に機能します。 Win32 アプリモデルで WinUI 3 だけを使用するには、winui **XAML アイランド** を使用して、winui コンテンツを別の UI フレームワーク (WINDOWS フォーム、WPF など) でホストする必要があります。 これは、アプリを進化させ、テクノロジを混在させる場合の正しいパスです。 ただし、WinUI の古い UI 全体を置き換える場合、アプリでは、WinUI をホストするための UI フレームワークを読み込まないようにする必要があります。

WinUI 3 は **、デスクトップアプリでの winui の追加に** 関するこの重要なフィードバックに対処します。 これにより、Win32 アプリは、スタンドアロン UI フレームワークとして、WinUI 3 を使用できるようになります。Windows フォームまたは WPF を読み込む必要はありません。

この集計では、WinUI 3 を使用すると、開発者は次のような組み合わせを簡単に組み合わせて使用できます。

* アプリモデル: UWP、Win32
* プラットフォーム: .NET またはネイティブ
* 言語: .NET (C \# 、Visual Basic)、標準 C++
* パッケージング: MSIX、Microsoft Store の AppX、パッケージ化されていません。
* 相互運用: winui 3 を使用して、既存の WPF、WinForms、および MFC アプリを、WinUI XAML アイランドを使用して拡張します。

詳細を知りたい場合は、Microsoft がこのロードマップをで共有してい <https://github.com/microsoft/microsoft-ui-xaml/blob/master/docs/roadmap.md> ます。

>[!div class="step-by-step"]
>[前へ](migrate-modern-applications.md)
>[次へ](example-migration.md)
