---
description: '詳細情報: クライアント アプリケーションでのデータ サービスの使用 (WCF Data Services)'
title: クライアント アプリケーションでのデータ サービスの使用 (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: f16b927a00aae55a3cb95630fc5d75a1c4c9e238
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791726"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>クライアント アプリケーションでのデータ サービスの使用 (WCF Data Services)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

Web ブラウザーに URI を入力することで、Open Data Protocol (OData) フィードを公開するサービスにアクセスできます。 URI はリソースのアドレスを提供し、要求メッセージがこれらのアドレスに送信されてリソースが表す基になるデータのアクセスまたは変更を行います。 ブラウザーは HTTP GET コマンドを発行して、要求されたリソースを OData フィードとして返します。 詳細については、「[Web ブラウザーからサービスへのアクセス](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)」を参照してください。  
  
 Web ブラウザーは OData サービスが予期されたデータを返すかどうかをテストするために便利ですが、データの作成、更新、および削除も行うことができる運用 OData サービスには、一般的にアプリケーション コードや Web ページのスクリプト言語を使用してアクセスします。 このトピックでは、クライアント アプリケーションから OData フィードにアクセスする方法の概要について説明します。  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>REST セマンティクスを使用したデータのアクセスおよび変更  

 OData は、OData フィードを公開するサービスと OData フィードを使用するアプリケーションの間の相互運用性を保証するのに役立ちます。 アプリケーションでは、特定の HTTP アクションの要求メッセージ、およびアクションを実行するエンティティ リソースのアドレスを指定する URI を送信して、OData ベースのサービス内のデータのアクセスおよび変更を行います。 エンティティ データを指定する必要がある場合、メッセージの本文に、エンコードされたペイロードとして明示的に指定します。  
  
### <a name="http-actions"></a>HTTP アクション  

 OData では、アドレス指定されたリソースが表すエンティティ データに対する操作の作成、読み取り、更新、および削除を実行する次の HTTP アクションがサポートされています。  
  
- **HTTP GET** - これは、ブラウザーからリソースにアクセスするときの既定のアクションです。 要求メッセージではペイロードは指定されず、要求されたデータを含むペイロードを含む応答メソッドが返されます。  
  
- **HTTP POST** - 新しいエンティティ データを指定されたリソースに挿入します。 挿入するデータは、要求メッセージのペイロードで指定されます。 応答メッセージのペイロードには、新しく作成されたエンティティのデータが含まれます。 これには自動生成されたキー値が含まれます。 ヘッダーには、新しいエンティティ リソースのアドレスを指定する URI も含まれます。  
  
- **HTTP DELETE** - 指定したリソースが表すエンティティ データを削除します。 ペイロードは要求メッセージおよび応答メッセージ内に存在しません。  
  
- **HTTP PUT** - 要求されたリソースの既存のエンティティ データを、要求メッセージのペイロードで指定された新しいデータで置き換えます。  
  
- **HTTP MERGE** - エンティティ データを変更するためだけに削除を実行した後にデータ ソースへの挿入を実行する非効率性を考慮して、OData では新しい HTTP MERGE アクションが導入されています。 要求メッセージのペイロードには、アドレス指定されたエンティティ リソースで変更する必要のあるプロパティが含まれます。 HTTP MERGE は HTTP 仕様で定義されていないので、OData 対応のサーバー以外で HTTP MERGE 要求をルーティングするには追加の処理が必要になる場合があります。  
  
 詳細については、[OData の操作](https://www.odata.org/documentation/odata-version-2-0/operations/)に関するページを参照してください。
  
### <a name="payload-formats"></a>ペイロード形式  

 HTTP PUT、HTTP POST、または HTTP MERGE 要求の場合、要求メッセージのペイロードは、データ サービスに送信するエンティティ データを含んでいます。 ペイロードのコンテンツは、メッセージのデータ形式によって異なります。 そのようなペイロードは、DELETE 以外のすべてのアクションに対する HTTP 応答にも含まれます。 OData では、サービスでのデータのアクセスおよび変更を行うために、次のペイロード形式がサポートされています。  
  
- **Atom** - Web フィード、ポッドキャスト、Wiki、および XML ベースのインターネット機能用に HTTP を介したデータ交換を有効にするために Atom 公開プロトコル (AtomPub) の拡張として OData で定義されている XML ベースのメッセージ エンコーディング。 詳細については、[OData のAtom 形式](https://www.odata.org/documentation/odata-version-2-0/atom-format/)に関するページを参照してください。
  
- **JSON** - JSON (JavaScript Object Notation) は、JavaScript プログラミング言語のサブセットに基づく軽量のデータ交換形式です。 詳細については、[OData のJSON 形式](https://www.odata.org/documentation/odata-version-2-0/json-format/)に関するページを参照してください。
  
 ペイロードのメッセージ形式は、HTTP 要求メッセージのヘッダーで要求されます。 詳細については、[OData の操作](https://www.odata.org/documentation/odata-version-2-0/operations/)に関するページを参照してください。
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>クライアント ライブラリを使用したデータのアクセスおよび変更  

 WCF Data Services には、.NET Framework ベースのクライアント アプリケーションおよび Silverlight ベースのクライアント アプリケーションから OData フィードを簡単に使用できるクライアント ライブラリが含まれています。 これらのライブラリは、HTTP メッセージの送受信を簡略化します。 また、メッセージ ペイロードをエンティティ データを表す CLR オブジェクトに変換します。 クライアント ライブラリには、 <xref:System.Data.Services.Client.DataServiceContext> および <xref:System.Data.Services.Client.DataServiceQuery%601>という 2 つのコア クラスがあります。 これらのクラスを使用すると、データ サービスをクエリして、返されるエンティティ データを CLR オブジェクトとして処理できます。 詳細については、「[WCF Data Services クライアント ライブラリ](wcf-data-services-client-library.md)」および「[WCF Data Services (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95))」を参照してください。  
  
 Visual Studio の **[サービス参照の追加]** ダイアログを使用して、参照をデータ サービスに追加できます。 このツールは、参照されたデータ サービスからサービス メタデータを要求し、データ サービスを表す <xref:System.Data.Services.Client.DataServiceContext> を生成します。また、エンティティを表すクライアント データ サービス クラスも生成します。 詳しくは、「[データ サービス クライアント ライブラリの生成](generating-the-data-service-client-library-wcf-data-services.md)」をご覧ください。  
  
 その他の種類のクライアント アプリケーションで OData フィードを使用するためのプログラミング ライブラリを利用できます。 OData SDK の詳細については、[OData SDK のサンプルコード](https://www.odata.org/ecosystem/#sdk)を参照してください。
  
## <a name="see-also"></a>関連項目

- [データ サービス リソースへのアクセス](accessing-data-service-resources-wcf-data-services.md)
- [クイック スタート](quickstart-wcf-data-services.md)
