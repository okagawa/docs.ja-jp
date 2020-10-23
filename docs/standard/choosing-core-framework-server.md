---
title: サーバー アプリ用 .NET 5 と .NET Framework の選択
description: サーバー アプリを構築するときに使用する .NET の実装を決定するのに役立つガイドです。
author: cartermp
ms.date: 10/06/2020
ms.openlocfilehash: d9dce0343f9d37e976472b818e896a5b0a661e76
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160452"
---
# <a name="net-5-vs-net-framework-for-server-apps"></a>サーバー アプリ用 .NET 5 と .NET Framework

サーバー側アプリのビルドでサポートされる実装には、.NET Framework と (.NET Core を含む) .NET 5 の 2 つがあります。 この 2 つは多数の同じコンポーネントを共有しているため、両者でコードを共有できます。 ただし、2 つには基本的な違いがあり、どちらを選択するかは実行内容によって決まります。 この記事では、それぞれを使用するタイミングに関するガイダンスを提供します。

.NET 5 は、次のような場合にお使いのサーバー アプリケーションで使用してください。

- クロスプラット フォームが必要である。
- マイクロサービスが対象である。
- Docker コンテナーを使用している。
- 高パフォーマンスでスケーラブルなシステムが必要である。
- 1 つのアプリケーションに複数の .NET バージョンが必要である。

次のような場合、サーバー アプリケーションには .NET Framework を使用します。

- 現在、アプリで .NET Framework を使用している (移行ではなく拡張することをお勧めします)。
- お使いのアプリで .NET 5 で使用できないサードパーティ製の .NET ライブラリや NuGet パッケージを使用している。
- お使いのアプリで、.NET 5 で使用できない .NET テクノロジを使用している。
- お使いのアプリで、.NET 5 がサポートされていないプラットフォームを使用している。

## <a name="when-to-choose-net-5"></a>.NET 5 を選択するタイミング

以下のセクションで、前述の .NET 5 を選択する理由について詳しく説明します。

### <a name="cross-platform-needs"></a>クロスプラットフォームの必要性

お使いのアプリケーション (Web またはサービス) を複数のプラットフォーム (Windows、Linux、macOS ) で実行する必要がある場合は、.NET 5 を使用します。

.NET 5 により、前述のオペレーティング システムがご自分の開発ワークステーションとしてサポートされています。 Visual Studio では、Windows および macOS 用の統合開発環境 (IDE) が用意されています。 また、macOS、Linux、および Windows 上で動作する Visual Studio Code も使用できます。 Visual Studio Code により、.NET 5 は IntelliSense、デバッグなどを含めサポートされています。 Sublime、Emacs、VI などのほとんどのサード パーティ製エディターは、.NET 5 で使用することができます。 これらのサード パーティ製エディターでは、[Omnisharp](https://www.omnisharp.net/) を使用して、エディターを IntelliSense にします。 また、コード エディターをまったく使用せずに、サポートされているすべてのプラットフォームで利用可能な [.NET Core CLI](../core/tools/index.md) を直接使用することもできます。

### <a name="microservices-architecture"></a>マイクロサービス アーキテクチャ

マイクロサービス アーキテクチャでは、サービスの境界を越えて、複数のテクノロジを組み合わせて使用できます。 このテクノロジの組み合わせによって、他のマイクロサービスやサービスと連携する新しいマイクロサービスに .NET 5 を段階的に採用することができます。 たとえば、.NET Framework、Java、Ruby などのモノリシックなテクノロジを使用して開発されたマイクロサービスまたはサービスを組み合わせることができます。

使用できるインフラストラクチャ プラットフォームは多数あります。 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) は、大規模で複雑なマイクロサービス システム向けに設計されています。 [Azure App Service](https://azure.microsoft.com/services/app-service/) は、ステートレス マイクロサービスに推奨されます。 「[コンテナー](#containers)」セクションで説明するように、Docker ベースのマイクロサービスの代替手段は、どのような種類のマイクロサービスのアプローチにも適しています。 .NET 5 は、これらすべてのプラットフォームでサポートされるため、お使いのマイクロサービスをホストするのに最適です。

マイクロサービス アーキテクチャの詳細については、「[.NET マイクロサービス:コンテナー化された .NET アプリケーションのアーキテクチャ](../architecture/microservices/index.md)」を参照してください。

### <a name="containers"></a>コンテナー

通常、コンテナーは、マイクロサービス アーキテクチャと組み合わせて使用されます。 コンテナーは、任意のアーキテクチャ パターンに従う Web アプリやサービスをコンテナー化するためにも使用できます。 Windows コンテナーには、.NET Framework も使用できますが、コンテナーにはモジュール方式で軽量な .NET 5 が適しています。 コンテナーを作成して展開する場合、そのイメージのサイズは .NET Framework より .NET 5 の方がはるかに小さくなります。 また、クロスプラットフォームであるため、Linux Docker コンテナーなどにサーバー アプリを展開することができます。

Docker コンテナーは、オンプレミスの Linux または Windows インフラストラクチャ、または [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) などのクラウド サービスでホストできます。 Azure Kubernetes Service は、コンテナーベースのアプリケーションの管理、調整、およびスケールをクラウドで行うことができます。

### <a name="high-performance-and-scalable-systems"></a>高パフォーマンスでスケーラブルなシステム

お使いのシステムに実現しうる最高のパフォーマンスとスケーラビリティが必要な場合、NET 5 と ASP.NET Core があなたに最適な選択肢です。 .NET は Windows Server および Linux 向けの高パフォーマンスなサーバー ランタイムであり、[TechEmpower のベンチマーク](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext)で高パフォーマンスの Web フレームワークとして上位に評価されました。

何百ものマイクロサービスが実行される可能性があるマイクロサービス アーキテクチャの場合は特に、パフォーマンスとスケーラビリティが重要です。 ASP.NET Core では、少数のサーバー/仮想マシン (VM) 数でシステムが動作します。 サーバー/VM が減るので、インフラストラクチャとホスティングにかかるコストを節約できます。

### <a name="side-by-side-net-versions-per-application-level"></a>アプリケーション レベルでの複数の .NET バージョン

複数バージョンの .NET に依存するアプリケーションをインストールする場合は、.NET 5 をお勧めします。 .NET 5 により、同じコンピューターに、異なるバージョンの .NET 5 ランタイムをサイドバイサイド インストールすることがサポートされています。 このサイドバイサイド インストールにより、複数のサービスを同じサーバー上に、また、それぞれのサービスを独自のバージョンの .NET 5 (または .NET Core 2.1 か 3.1) に配置することができます。 また、アプリケーションのアップグレードと IT 運用に関係するリスクとコストを軽減できます。

.NET Framework で、サイドバイサイド インストールはできません。 これは Windows のコンポーネントであり、1 台のコンピューターには同時に 1 つのバージョンしか存在させることができません。 .NET Framework の前のバージョンは、各バージョンに置き換えられます。 新しいバージョンの .NET Framework を対象とする新しいアプリをインストールすると、以前のバージョンが置き換えられてしまうために、そのコンピューターで実行されている既存のアプリが破損してしまう場合があります。

## <a name="when-to-choose-net-framework"></a>どのような場合に .NET Framework を選択すべきか

.NET 5 は、新しいアプリケーションやアプリケーション パターンに大きな利益をもたらします。 ただし、.NET Framework は既存の多くのシナリオで一般的に選択されているため、すべてのサーバー アプリケーションで .NET Framework は .NET 5 に置き換えられていません。

### <a name="current-net-framework-applications"></a>現在の .NET Framework アプリケーション

ほとんどの場合、お使いの既存のアプリケーションを .NET 5 に移行する必要はありません。 .NET 5 は、ASP.NET Core で新しい Web サービスを作成するなど、既存のアプリケーションを拡張するような場合に使用することをお勧めします。

### <a name="third-party-libraries-or-nuget-packages-not-available-for-net-5"></a>.NET 5 で使用できないサードパーティ製のライブラリや NuGet パッケージ

.NET Standard を使用すると、.NET 5 を含め、すべての .NET 実装全体でコードを共有できます。 NET Standard 2.0 の互換モードを使用すると、.NET Standard および .NET 5 プロジェクトで .NET Framework ライブラリを参照できます。 詳細については、「[.NET Framework ライブラリのサポート](whats-new/whats-new-in-dotnet-standard.md#support-for-net-framework-libraries)」を参照してください。

ライブラリまたは NuGet パッケージで、.NET Standard や .NET 5 にないテクノロジが使用されている場合にのみ、.NET Framework は使用してください。

### <a name="net-technologies-not-available-for-net-5"></a>.NET 5 で使用できない .NET のテクノロジ

一部の .NET Framework テクノロジは .NET 5 では使用できません。 .NET 5 にはない最も一般的なテクノロジを、以下に列挙します。

- ASP.NET Web フォーム アプリケーション:ASP.NET Web フォームは、.NET Framework でのみ使用できます。 ASP.NET Core は、ASP.NET Web フォームに使用できません。

- ASP.NET Web ページ アプリケーション:ASP.NET Web ページは、ASP.NET Core に含まれていません。

- WCF サービスの実装。 .NET 5 から WCF サービスを使用する [WCF クライアント ライブラリ](https://github.com/dotnet/wcf)がありますが、現在 WCF サーバーの実装は、.NET Framework でのみ利用できます。

- ワークフローに関連するサービス:Windows Workflow Foundation (WF)、ワークフロー サービス (1 つのサービスに WCF と WF) および WCF Data Services (旧称: ADO.NET Data Services) は、NET Framework でのみ使用できます。

- 言語のサポート:Visual Basic と F# は現在 .NET 5 でサポートされていますが、サポートされないプロジェクトの種類もあります。 サポートされるプロジェクト テンプレートの一覧については、[dotnet new のテンプレート オプション](../core/tools/dotnet-new.md#arguments)に関するセクションを参照してください。

詳細については、[.NET 5 で使用できない .NET Framework テクノロジ](../core/porting/net-framework-tech-unavailable.md)に関する記事を参照してください。

### <a name="platform-doesnt-support-net-5"></a>.NET 5 がプラットフォームでサポートされない

Microsoft やサードパーティ製のプラットフォームの中には、.NET 5 がサポートされていないものもあります。 一部の Azure サービスにより、.NET 5 ではまだ使用できない SDK が提供されています。 そのような場合は、クライアント SDK の代わりに同等の REST API を使用できます。

## <a name="see-also"></a>関連項目

- [ASP.NET と ASP.NET Core の選択](/aspnet/core/choose-aspnet-framework)
- [.NET Framework を対象とする ASP.NET Core](/aspnet/core/introduction-to-aspnet-core?view=aspnetcore-2.2&preserve-view=true#aspnet-core-targeting-net-framework)
- [ターゲット フレームワーク](frameworks.md)
- [.NET の概要](../core/introduction.md)
- [.NET Framework から .NET 5 への移植](../core/porting/index.md)
- [.NET および Docker の概要](../core/docker/introduction.md)
- [.NET コンポーネントの概要](components.md)
- [.NET マイクロサービス:コンテナー化された .NET アプリケーションのアーキテクチャ](../architecture/microservices/index.md)
