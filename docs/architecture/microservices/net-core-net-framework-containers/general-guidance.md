---
title: 一般的なガイダンス
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | 一般的なガイダンス'
ms.date: 01/13/2021
ms.openlocfilehash: 4fd2d936c524cb3e5ae463038eaffe88b459d2bd
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98187952"
---
# <a name="general-guidance"></a>一般的なガイダンス

このセクションでは、.NET 5 または .NET Framework を選択する場合の概要を示します。 後続のセクションでこれらの選択の詳細について説明します。

次の場合には、コンテナー化された Docker サーバー アプリケーションで、.NET 5 と Linux または Windows のコンテナーを併用します。

- クロスプラット フォームが必要である。 たとえば、Linux と Windows のコンテナーの両方を使用する場合。

- アプリケーション アーキテクチャがマイクロサービスに基づく場合。

- コンテナーを高速で起動する必要があり、かつコンテナーあたりのフットプリントを小さくして密度を高めたり、ハードウェア ユニットあたりのコンテナーを増やしてコストを削減したりしたい場合。

つまり、コンテナー化された .NET アプリケーションを新たに作成する場合には、.NET 5 を既定の選択肢として考慮する必要があります。 これには多くの利点があり、コンテナーの理念や作業スタイルとぴったりと適合します。

さらに .NET 5 を使用する利点は、同じマシンで複数の .NET バージョンのアプリケーションを同時に実行できることです。 この利点は、コンテナーを使用しないサーバーまたは VM にとってはさらに重要になります。コンテナーは、アプリが必要とする .NET バージョンを特定するためです。 (基礎となる OS と互換性がある場合。)

次の場合には、コンテナー化された Docker サーバー アプリケーションで、.NET Framework を使用します。

- 現在、アプリケーションで .NET Framework を使用し、Windows で強い依存関係がある場合。

- .NET 5 でサポートされていない Windows API を使用する必要がある。

- .NET 5 で使用できないサードパーティ製の .NET ライブラリまたは NuGet パッケージを使用する必要がある。

Docker で .NET Framework を使用すると、展開に関する問題を最小限に抑えて、展開のエクスペリエンスを改善できます。 この ["リスト アンド シフト" シナリオ](https://aka.ms/liftandshiftwithcontainersebook)は、ASP.NET WebForms、MVC Web アプリ、WCF (Windows Communication Foundation) サービスなどの従来の .NET Framework を使用して開発されたレガシー アプリケーションをコンテナー化する場合に重要です。

### <a name="additional-resources"></a>その他の技術情報

- **電子書籍: Modernize existing .NET Framework applications with Azure and Windows Containers (Azure および Windows コンテナーで既存の .NET Framework アプリケーションを最新化する)**  
    <https://aka.ms/liftandshiftwithcontainersebook>

- **サンプル アプリ:Windows コンテナーを使用した従来の ASP.NET Web アプリの最新化**  
    <https://aka.ms/eshopmodernizing>

>[!div class="step-by-step"]
>[前へ](index.md)
>[次へ](net-core-container-scenarios.md)
