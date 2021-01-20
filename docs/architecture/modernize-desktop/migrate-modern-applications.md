---
title: 最新のデスクトップアプリケーションの移行
description: 最新のデスクトップアプリケーションの移行プロセスについて理解しておく必要があること。
ms.date: 01/19/2021
ms.openlocfilehash: b5bea6e601dc040adfd8ed410320a3416cb3372e
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615764"
---
# <a name="migrating-modern-desktop-applications"></a>最新のデスクトップアプリケーションの移行

この章では、既存のアプリケーションを .NET Framework から .NET に移行する際に直面する可能性がある、最も一般的な問題と課題について説明します。

複雑なデスクトップアプリケーションは、独立して動作せず、ローカルコンピューターまたはリモートサーバー上に存在する可能性があるサブシステムとの対話を必要とします。 多くの場合、永続化ストレージとしてローカルまたはリモートで接続するには、何らかの種類のデータベースが必要になります。 インターネットとサービス指向アーキテクチャの向上により、アプリケーションは、リモートサーバーまたはクラウドに存在する何らかのサービスに接続することが一般的です。 一部の機能を実装するには、コンピューターのファイルシステムにアクセスする必要がある場合があります。 または、アプリケーションの外部にある COM オブジェクト内に存在する機能を使用している場合もあります。たとえば、アプリに Office アセンブリを統合している場合は、一般的なシナリオです。

また、.NET Framework と .NET によって公開される API サーフェイスには違いがあり、.NET Framework で利用できる一部の機能は .NET では使用できません。 そのため、移行を計画する際には、それらを把握して考慮することが重要です。

## <a name="configuration-files"></a>構成ファイル

構成ファイルを利用すると、実行時に読み取られるプロパティのセットを格納して、アプリケーションの動作に影響を与えることができます。たとえば、データベースを配置する場所や、ループを実行する回数などです。 この手法の利点は、アプリケーションの一部の側面を再書き込みと再コンパイルせずに変更できることです。 これは、たとえば、同じアプリコードが、特定の構成値のセットを持つ開発環境で実行され、別の構成値を持つ運用環境で実行される場合に便利です。

### <a name="configuration-on-net-framework"></a>.NET Framework での構成

動作中の .NET Framework デスクトップアプリケーションがある場合、名前空間からクラスを介してアクセスされる *app.config* ファイルがある可能性があり <xref:System.Configuration.AppSettingsSection> `System.Configuration` ます。

.NET Framework インフラストラクチャ内には、親からプロパティを継承する構成ファイルの階層があります。 子孫構成ファイルで使用またはオーバーライドできる多くのプロパティと構成セクションを定義する *machine.config* ファイルを見つけることができます。

### <a name="configuration-on-net"></a>.NET での構成

.NET の世界では、 *machine.config* ファイルはありません。 また、以前の方法の名前空間を使用し続けることもできますが、 <xref:System.Configuration> <xref:Microsoft.Extensions.Configuration> 多くの拡張機能を備えた最新のに切り替えることを検討してください。

構成 API は、構成プロバイダーの概念をサポートします。構成プロバイダーは、構成の読み込みに使用されるデータソースを定義します。 組み込みプロバイダーには、次のような種類があります。

- メモリ内 .NET オブジェクト
- INI ファイル
- JSON ファイル
- XML ファイル
- コマンド ライン引数
- 環境変数
- 暗号化されたユーザーストア

 または、独自のものを作成することもできます。

新しい構成では、複数レベルの階層にグループ化できる名前と値のペアの一覧を使用できます。 格納されている値は文字列にマップされます。また、設定をカスタムの plain old CLR object (POCO) オブジェクトに逆シリアル化できる組み込みのバインディングがサポートされています。

<xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>オブジェクトを使用すると、優先順位ルールを使用して優先順位を解決することで、アプリケーションに必要な構成プロバイダーをいくつでも追加できます。 そのため、コードに最後に追加したプロバイダーが他のプロバイダーよりも優先されます。 これは、開発、テスト、および運用環境用にさまざまな構成を定義し、コード内の1つの関数でそれらを管理できるため、さまざまな実行環境を管理するための優れた機能です。

### <a name="migrating-configuration-files"></a>構成ファイルの移行

既存の app.config XML ファイルを引き続き使用することができます。 ただし、この機会を利用して構成を移行することで、.NET に加えられたいくつかの拡張機能を活用できます。

旧形式の *app.config* から新しい構成ファイルに移行するには、XML 形式と JSON 形式のどちらかを選択する必要があります。

XML を選択した場合、変換は簡単です。 コンテンツは同じであるため、 *app.config* ファイルを XML で型として保存するだけです。 次に、AppSettings を参照するコードを変更して、クラスを使用し `ConfigurationBuilder` ます。 この変更は簡単です。

JSON 形式を使用し、手動で移行しない場合は、 [dotnet](https://www.nuget.org/packages/dotnet-config2json/) というツールを .net で使用できます。このツールを使用すると、 *app.config* ファイルを JSON 構成ファイルに変換できます。

また、 *machine.config* ファイルで定義された構成セクションを使用すると、いくつかの問題が発生する場合があります。 たとえば、次のような構成を考えてみます。

```xml
<configuration>
    <system.diagnostics>
        <switches>
            <add name="General" value="4" />
        </switches>
        <trace autoflush="true" indentsize="2">
            <listeners>
                <add name="myListener"
                     type="System.Diagnostics.TextWriterTraceListener,
                           System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
                     initializeData="MyListener.log"
                     traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />
            </listeners>
        </trace>
    </system.diagnostics>
</configuration>
```

この構成を .NET に対して行うと、例外が発生します。

> 認識されない構成セクションシステムです。診断

この例外が発生するのは、そのセクションと、そのセクションを処理するアセンブリが、現在は存在しない *machine.config* ファイルで定義されているためです。

この問題を簡単に解決するには、古い *machine.config* から新しい構成ファイルにセクションの定義をコピーします。

```xml
<configSections>
    <section name="system.diagnostics"
             type="System.Diagnostics.SystemDiagnosticsSection,
                   System, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
</configSections>
```

## <a name="accessing-databases"></a>データベースへのアクセス

ほとんどすべてのデスクトップアプリケーションには、何らかの種類のデータベースが必要です。 デスクトップの場合は、デスクトップアプリとデータベースエンジンの間の直接接続を使用して、クライアントサーバーアーキテクチャを検索するのが一般的です。 これらのデータベースは、異なるユーザー間で情報を共有する必要があるかどうかに応じて、ローカルでもリモートでもかまいません。

コードの観点からは、開発者がデータベースに接続し、クエリを実行し、データベースを更新できるようにするためのテクノロジとフレームワークが数多くあります。

Windows デスクトップアプリケーションについて説明している最も一般的なデータベースの例として、Microsoft Access と Microsoft SQL Server があります。 デスクトップに対して20年を超える経験を持っている場合、ODBC、OLEDB、RDO、ADO、ADO.NET、LINQ、Entity Framework などの名前がよく知られています。

### <a name="odbc"></a>ODBC

Microsoft が .NET Standard 2.0 と互換性のあるライブラリを提供しているため、.NET で ODBC を使用し続けることができ `System.Data.Odbc` ます。

### <a name="ole-db"></a>OLE DB

[OLE DB](/previous-versions/windows/desktop/ms722784(v=vs.85)) は、一貫した方法でさまざまなデータソースにアクセスするための優れた方法です。 しかし、これは Windows 専用のテクノロジであり、.NET などのクロスプラットフォームテクノロジに最適ではないため、COM に基づいていました。 SQL Server バージョン2014以降でもサポートされていません。 このような理由から、OLE DB は .NET ではサポートされません。

### <a name="adonet"></a>ADO.NET

.NET の既存のデスクトップコードから ADO.NET を使用することもできます。 一部の NuGet パッケージのみを更新する必要があります。

### <a name="ef-core-vs-ef6"></a>EF Core と EF6

現在サポートされているバージョンの Entity Framework (EF)、Entity Framework 6 (EF6)、および EF Core が2つあります。

.NET Framework 世界の一部としてリリースされた最新のテクノロジは Entity Framework であり、6.4 は最新バージョンです。 .NET Core を起動すると、Microsoft は Entity Framework に基づいて新しいデータアクセススタックをリリースし、Entity Framework Core と呼ばれるようになりました。

EF 6.4 と EF Core .NET Framework と .NET の両方で使用できます。 そのため、2つの判断に役立つデシジョンドライバーは何ですか。

EF 6.3 は、.NET で実行できる EF6 の最初のバージョンであり、クロスプラットフォームで動作します。 実際、このリリースの主な目的は、EF6 を使用する既存のアプリケーションを .NET に簡単に移行できるようにすることでした。

EF Core は EF6 のような開発者エクスペリエンスを提供するように設計されました。 最上位レベルの API のほとんどは同じままなので、EF6 を使用していた開発者にとって EF Core は使い慣れたものと感じるでしょう。

互換性がありますが、決定を行う前に、確認する必要がある実装に違いがあります。
詳細については、「 [Compare EF Core & EF6](/ef/efcore-and-ef6/)」を参照してください。

次の場合に EF Core を使用することをお勧めします。

* アプリには .NET の機能が必要です。
* EF Core では、そのアプリに必要な機能がすべてサポートされています。

次の条件の両方に該当する場合、EF 6 の使用を検討してください。

* アプリは Windows で実行され、4.0 以降 .NET Framework ます。
* EF6 では、そのアプリに必要な機能がすべてサポートされています。

### <a name="relational-databases"></a>リレーショナル データベース

#### <a name="sql-server"></a>SQL Server

SQL Server は、何年も前にデスクトップ向けに開発していた場合に、選択したデータベースの1つになりました。 .NET Framework でを使用すると、 <xref:System.Data.SqlClient> データベース固有のプロトコルをカプセル化した SQL Server のバージョンにアクセスできます。

.NET では、.NET Framework に存在する `SqlClient` がライブラリ内に存在するものと完全に互換性のある新しいクラスを見つけることができ <xref:Microsoft.Data.SqlClient> ます。 ここでは、 [Microsoft. Data. SqlClient](https://www.nuget.org/packages/Microsoft.Data.SqlClient/) NuGet パッケージへの参照を追加し、名前空間の名前を変更して、すべてを想定どおりに動作させる必要があります。

#### <a name="microsoft-access"></a>Microsoft Access

Microsoft Access は、高度でスケーラブルな SQL Server が不要になったときに、何年も使用されています。 ライブラリを使用して Microsoft Access に接続することもでき <xref:System.Data.Odbc> ます。

## <a name="consuming-services"></a>サービスの利用

サービス指向アーキテクチャの導入により、デスクトップアプリケーションは、クライアント/サーバーモデルから3層アプローチへの進化を開始しました。 クライアントとサーバーの間のアプローチでは、通常は1つの EXE ファイル内にビジネスロジックを保持するクライアントから直接データベース接続が確立されます。 一方、3層アプローチは、ビジネスロジックとデータベースアクセスを実装する中間サービスレイヤーを確立して、セキュリティ、スケーラビリティ、および再利用性を高めることができます。 レイヤーアプローチは、データのデータセットを直接操作するのではなく、データ転送を実装する手段として、コントラクトと型オブジェクトを実装する一連のサービスに依存します。

WCF サービスを使用しているデスクトップアプリケーションがあり、それを .NET に移行する場合は、いくつかの点を考慮する必要があります。

まず、サービスにアクセスするための構成を解決する方法を説明します。 構成は .NET では異なるため、構成ファイルでいくつかの更新を行う必要があります。

次に、Visual Studio 2019 に存在する新しいツールを使用してサービスクライアントを再生成する必要があります。 この手順では、同期操作の生成をアクティブ化して、クライアントが既存のコードと互換性を持つようにする必要があります。

移行後に、.NET 上に存在しないライブラリがあることがわかった場合は、 [Microsoft の互換性](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) に関する NuGet パッケージへの参照を追加し、不足している関数があるかどうかを確認します。

クラスを使用して web サービス呼び出しを実行している場合は <xref:System.Net.WebRequest> 、.net にいくつかの違いがある可能性があります。 代わりに、システムの .Net. HttpClient を使用することをお勧めします。

## <a name="consuming-a-com-object"></a>COM オブジェクトの使用

現時点では、.NET で使用するために、Visual Studio 2019 から COM オブジェクトへの参照を追加する方法はありません。 そのため、プロジェクトファイルを手動で変更する必要があります。

次の `COMReference` 例のように、プロジェクトファイル内に構造体を挿入します。

```xml
<ItemGroup>
    <COMReference Include="MSHTML">
        <Guid>{3050F1C5-98B5-11CF-BB82-00AA00BDCE0B}\</Guid>
        <VersionMajor>4</VersionMajor>
        <VersionMinor>0</VersionMinor>
        <Lcid>0</Lcid>
        <WrapperTool>primary</WrapperTool>
        <Isolated>false</Isolated>
    </COMReference>
</ItemGroup>
```

## <a name="more-things-to-consider"></a>その他の考慮事項

.NET Framework ライブラリで利用できるいくつかのテクノロジは、.NET Core または .NET 5 では使用できません。 コードがこれらのテクノロジの一部に依存している場合は、このセクションで説明する別の方法を検討してください。

[Windows 互換機能パック](../../core/porting/windows-compat-pack.md)は、以前に .NET Framework でのみ使用できる api へのアクセスを提供します。 .NET Core と .NET Standard のプロジェクトで使用できます。

API の互換性の詳細については、「」の互換性に影響する変更点と非推奨の Api に関するドキュメントを参照して <https://docs.microsoft.com/dotnet/core/compatibility/fx-core> ください。

### <a name="appdomains"></a>AppDomain

アプリケーション ドメイン (AppDomains) はアプリを互いに分離します。 AppDomains ではランタイムサポートが必要であり、コストが高くなります。 追加のアプリドメインの作成はサポートされていません。 コードの分離には、代わりの方法として、プロセスの分離やコンテナーの利用をお勧めします。 アセンブリの動的読み込みには、新しい <xref:System.Runtime.Loader.AssemblyLoadContext> クラスをお勧めします。

コードを .NET Framework から簡単に移行できるように、.NET では API サーフェイスの一部を公開して `AppDomain` います。 API の中には、正常に機能するもの (<xref:System.AppDomain.UnhandledException?displayProperty=nameWithType> など)、処理を行わないメンバー (<xref:System.AppDomain.SetCachePath%2A> など)、<xref:System.PlatformNotSupportedException> をスローするもの (<xref:System.AppDomain.CreateDomain%2A> など) があります。

### <a name="remoting"></a>リモート処理

.NET リモート処理は、サポートされなくなった AppDomain 間通信に使用されました。 また、リモート処理にはランタイム サポートが必要で、維持するのに高いコストがかかります。 このような理由から、.net では .NET リモート処理がサポートされていません。

プロセス間の通信については、またはクラスなど、リモート処理の代わりにプロセス間通信 (IPC) メカニズムを検討する必要があり <xref:System.IO.Pipes?displayProperty=nameWithType> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> ます。

マシン間では、代替方法としてネットワーク ベースのソリューションを使用してください。 できれば、HTTP など、オーバーヘッドの少ないプレーンテキストプロトコルを使用することをお勧めします。 この場合、ASP.NET Core で使用される Web サーバーの Kestrel Web Server も選択できます。

### <a name="code-access-security-cas"></a>コード アクセス セキュリティ (CAS)

サンドボックスは、ランタイムまたはフレームワークに依存して、マネージアプリケーションまたはライブラリが使用または実行するリソースを制限します。 .NET ではサポートされていません。

オペレーティングシステムによって提供されるセキュリティ境界 (仮想化、コンテナー、ユーザーアカウントなど) を使用して、最小限の特権セットでプロセスを実行します。

### <a name="security-transparency"></a>セキュリティ透過性

CAS と同様に、セキュリティ透過性はサンドボックス コードをセキュリティ クリティカルなコードから宣言的に分離しますが、現在はセキュリティ境界としてはサポートされていません。

仮想化、コンテナー、ユーザーアカウントなど、オペレーティングシステムによって提供されるセキュリティ境界を使用して、最小限の特権を持つプロセスを実行します。

>[!div class="step-by-step"]
>[前へ](whats-new-dotnet.md )
>[次へ](windows-migration.md)
