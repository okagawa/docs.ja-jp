---
description: 詳細については、.NET Framework の構成ファイルスキーマに関するページを参照してください。
title: .NET Framework の構成ファイル スキーマ
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: eac6d14f29f5ae0eeb65efe5a1416b8f40583be3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729954"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>.NET Framework の構成ファイル スキーマ

構成ファイルは、設定を変更し、アプリのポリシーを設定するために使用できる標準 XML ファイルです。 .NET Framework の構成スキーマは、アプリの動作を制御するために構成ファイルで使用できる要素で構成されます。 このセクションの目次は、スキーマ、起動時の階層、ランタイム、ネットワーク、およびその他の種類の構成設定を反映しています。

構成ファイルの種類、形式、および場所の詳細については、「 [アプリの構成](../index.md)」を参照してください。 構成ファイルを直接編集する場合は、XML に関する知識が必要です。

> [!IMPORTANT]
> 構成ファイルの XML タグおよび属性では、大文字と小文字が区別されます。

## <a name="in-this-section"></a>このセクションの内容

[**\<configuration>** Element](configuration-element.md)\
すべての構成ファイルの最上位要素。

[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md)\
構成レベルでのアセンブリ バインディング ポリシーを指定します。

[**\<linkedConfiguration>** Element](linkedconfiguration-element.md)\
インクルードする構成ファイルを指定します。

[スタートアップ設定スキーマ](./startup/index.md)\
使用する共通言語ランタイムのバージョンを指定する要素。

[ランタイム設定スキーマ](./runtime/index.md)\
アセンブリバインディングとランタイム動作を構成する要素。

[ネットワーク設定スキーマ](./network/index.md)\
.NET Framework がインターネットに接続する方法を指定する要素。

[暗号化設定スキーマ](./cryptography/index.md)\
アルゴリズムのフレンドリ名を、暗号化アルゴリズムを実装するクラスにマップする要素。

[構成セクションのスキーマ](configuration-sections-schema.md)\
カスタム設定の構成セクションを作成して使用するために使用される要素。

[トレースおよびデバッグ設定のスキーマ](./trace-debug/index.md)\
トレーススイッチとリスナーを指定する要素。

[コンパイラおよび言語プロバイダー設定スキーマ](./compiler/index.md)\
使用可能な言語プロバイダーのコンパイラ構成を指定する要素。

[アプリケーション設定スキーマ](application-settings-schema.md)\
Windows フォームまたは ASP.NET アプリケーションで、アプリケーションスコープの設定とユーザースコープの設定を格納および取得できるようにする要素。

[アプリ設定スキーマ](./appsettings/index.md)\
ファイル パス、XML Web サービス URL、またはアプリケーションのその他のカスタム構成情報など、カスタム アプリケーションの設定が含まれています。

[Web 設定スキーマ](./web/index.md)\
IIS などのホストアプリケーションで ASP.NET がどのように動作するかを構成するための要素。 *Aspnet.config* ファイルで使用します。

[Windows フォーム構成スキーマ](winforms/index.md)\
Windows フォームアプリケーション構成セクション内のすべての要素。マルチモニターや高 DPI のサポートなどのカスタマイズが含まれます。

[WCF 構成スキーマ](./wcf/index.md)\
WCF サービスおよびクライアントアプリケーションを構成できるすべての要素。

[WCF ディレクティブの構文](./wcf-directive/index.md)\
`@ServiceHost`.Svc コンパイラによって使用されるページ固有の属性を定義するディレクティブについて説明します。

[WIF 構成スキーマ](windows-identity-foundation/index.md)\
Windows Identity Foundation (WIF) 構成スキーマのすべての要素。

## <a name="related-sections"></a>関連項目

[リモート処理設定スキーマ](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))\
リモート処理を実装するクライアント アプリケーションとサーバー アプリケーションを構成する要素について説明します。

[ASP.NET 設定スキーマ](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))\
ASP.NET Web アプリケーションの動作を制御する要素について説明します。

[Web サービス設定スキーマ](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))\
ASP.NET Web サービス、およびそれらのクライアントの動作を制御する要素について説明します。

[.NET Framework アプリの構成](/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))\
セキュリティ、アセンブリのバインディング、および .NET Framework のリモート処理を構成する方法について説明します。
