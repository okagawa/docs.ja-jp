---
title: '方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 0aea4c21b5ea34cb0e8d944d37c879e918d6b27e
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800593"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a>方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する (WCF Data Services)

WCF Data Services は、エンティティ データをデータ サービスとして公開します。 データ ソースがリレーショナル データベースの場合、このエンティティ データは ADO.NET Entity Framework によって提供されます。 このトピックでは、既存のデータベースに基づき、このデータ モデルを使用して新しいデータ サービスを作成する Visual Studio Web アプリケーションで Entity Framework ベースのデータ モデルを作成する方法について説明します。

Entity Framework は、Visual Studio プロジェクトの外部に Entity Framework モデルを生成できるコマンド ライン ツールも提供します。 詳細については、[EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)」を参照してください。

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a>既存のデータベースに基づく Entity Framework モデルを既存の Web アプリケーションに追加するには

1. **[プロジェクト]** メニューの **[追加]**  >  **[新しい項目]** をクリックします。

2. **[テンプレート]** ペインの **[データ]** カテゴリをクリックして、 **[ADO.NET Entity Data Model]** をクリックします。

3. モデル名を入力して、 **[追加]** をクリックします。

     Entity Data Model ウィザードの先頭ページが表示されます。

4. **[モデルのコンテンツの選択]** ダイアログ ボックスで **[データベースから生成]** を選択します。 その後、 **[次へ]** をクリックします。

5. **[新しい接続]** ボタンをクリックします。

6. **[接続のプロパティ]** ダイアログ ボックスでサーバー名を入力し、認証方法を選択します。データベース名を入力して、 **[OK]** をクリックします。

     指定したデータベース接続の設定に従って、 **[データ接続の選択]** ダイアログ ボックスが更新されます。

7. **[エンティティ接続設定に名前を付けて App.Config に保存]** チェックボックスがオンになっていることを確認します。 その後、 **[次へ]** をクリックします。

8. **[データベース オブジェクトの選択]** ダイアログ ボックスで、データ サービスで公開するすべてのデータベース オブジェクトを選択します。

    > [!NOTE]
    > データ モデルに含まれるオブジェクトは、データ サービスによって自動的には公開されません。 これらのオブジェクトは、サービス自身によって明示的に公開される必要があります。 詳細については、「[データ サービスの構成](configuring-the-data-service-wcf-data-services.md)」を参照してください。

9. **[完了]** をクリックしてウィザードを終了します。

     特定のデータベースに基づく既定のデータ モデルが作成されます。 Entity Framework では、データ モデルをカスタマイズできます。 詳しくは、「[Entity Data Model ツールのタスク](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100))」をご覧ください。

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a>新しいデータ モデルを使用してデータ サービスを作成するには

1. データ モデルを表す .edmx ファイルを Visual Studio で開きます。

2. **モデル ブラウザー**でモデルを右クリックし、 **[プロパティ]** をクリックしてエンティティ コンテナーの名前を確認します。

3. **ソリューション エクスプローラー**で、ASP.NET プロジェクトの名前を右クリックし、 **[追加]**  >  **[新しい項目]** をクリックします。

4. **[新しい項目の追加]** ダイアログ ボックスで、 **[Web]** カテゴリの **[WCF Data Service]** テンプレートを選択します。

   ![Visual Studio 2015 の WCF Data Service 項目テンプレート](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF Data Service** テンプレートは Visual Studio 2015 で使用できますが、Visual Studio 2017 以降では使用できません。

5. サービスの名前を指定して、 **[OK]** をクリックします。

     Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。 既定では、コード エディターのウィンドウが開きます。

6. データ サービスのコードで、データ サービスを定義するクラスの定義内のコメント `/* TODO: put your data source class name here */` を <xref:System.Data.Objects.ObjectContext> クラスから継承する型で置き換えます。この型はデータ モデルのエンティティ コンテナー (手順 2 で確認したコンテナー) です。

7. データ サービスのコードで、承認されたクライアントがデータ サービスによって公開されているエンティティ セットにアクセスできるようにします。 詳細については、「[データ サービスの作成](creating-the-data-service.md)」を参照してください。

8. Web ブラウザーを使用して Northwind.svc データ サービスをテストするには、トピック「[Web ブラウザーからサービスへのアクセス](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)」の手順に従います。

## <a name="see-also"></a>関連項目

- [WCF Data Services の定義](defining-wcf-data-services.md)
- [Data Services プロバイダー](data-services-providers-wcf-data-services.md)
- [方法: リフレクション プロバイダーを使用してデータ サービスを作成する](create-a-data-service-using-rp-wcf-data-services.md)
- [方法: LINQ to SQL データ ソースを使用してデータ サービスを作成する](create-a-data-service-using-linq-to-sql-wcf.md)
