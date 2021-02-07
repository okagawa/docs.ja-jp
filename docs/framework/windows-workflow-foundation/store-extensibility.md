---
description: '詳細情報: ストアの機能拡張'
title: ストア拡張
ms.date: 03/30/2017
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
ms.openlocfilehash: f04c466224aacd1c8f755e7aa60b18846d0c7180
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755227"
---
# <a name="store-extensibility"></a>ストア拡張

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を使用して、永続性データベースのインスタンスをクエリする場合に使用できるカスタムのアプリケーション固有のプロパティを昇格できます。 プロパティを昇格することで、データベース内の特殊なビュー内で値が使用できるようになります。 これらの昇格したプロパティ (ユーザー クエリで使用できるプロパティ) は、単純型 (Int64、Guid、String、DateTime など) またはシリアル化されたバイナリ型 (byte[]) になる場合があります。

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> クラスには <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> メソッドがあり、クエリで使用できるプロパティとしてプロパティを昇格するために使用できます。 次の例は、ストア拡張のエンド ツー エンドの例です。

1. この例のシナリオでは、ドキュメント処理 (DP) アプリケーションにワークフローがあり、それぞれがドキュメント処理にカスタム アクティビティを使用しています。 これらのワークフローは、エンド ユーザーから見える必要がある一連の状態変数を備えています。 これを実現するために、DP アプリケーションには <xref:System.Activities.Persistence.PersistenceParticipant> 型を持つインスタンス拡張機能があり、状態変数を提供するアクティビティによって使用されます。

    ```csharp
    class DocumentStatusExtension : PersistenceParticipant
    {
        public string DocumentId;
        public string ApprovalStatus;
        public string UserName;
        public DateTime LastUpdateTime;
    }
    ```

2. 次に、新しい機能拡張がホストに追加されます。

    ```csharp
    static Activity workflow = CreateWorkflow();
    WorkflowApplication application = new WorkflowApplication(workflow);
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();
    application.Extensions.Add(documentStatusExtension);
    ```

     カスタムの永続参加要素を追加する方法の詳細については、 [永続参加](persistence-participants.md) 要素のサンプルを参照してください。

3. DP アプリケーションのカスタムアクティビティは、 **Execute** メソッドにさまざまな状態フィールドを設定します。

    ```csharp
    public override void Execute(CodeActivityContext context)
    {
        // ...
        context.GetExtension<DocumentStatusExtension>().DocumentId = Guid.NewGuid();
        context.GetExtension<DocumentStatusExtension>().UserName = "John Smith";
        context.GetExtension<DocumentStatusExtension>().ApprovalStatus = "Approved";
        context.GetExtension<DocumentStatusExtension>().LastUpdateTime = DateTime.Now();
        // ...
    }
    ```

4. ワークフローインスタンスが永続化ポイントに到達すると、 **Documentstatusextension** 永続化参加要素の **collectvalues** メソッドによって、これらのプロパティが永続性データコレクションに保存されます。

    ```csharp
    class DocumentStatusExtension : PersistenceParticipant
    {
        const XNamespace xNS = XNamespace.Get("http://contoso.com/DocumentStatus");

        protected override void CollectValues(out IDictionary<XName, object> readWriteValues, out IDictionary<XName, object> writeOnlyValues)
        {
            readWriteValues = new Dictionary<XName, object>();
            readWriteValues.Add(xNS.GetName("UserName"), this.UserName);
            readWriteValues.Add(xNS.GetName("ApprovalStatus"), this.ApprovalStatus);
            readWriteValues.Add(xNS.GetName("DocumentId"), this.DocumentId);
            readWriteValues.Add(xNS.GetName("LastModifiedTime"), this.LastUpdateTime);

            writeOnlyValues = null;
        }
        // ...
    }
    ```

    > [!NOTE]
    > これらのプロパティはすべて、 **SaveWorkflowCommand** コレクションを通じて永続化フレームワークによって **SqlWorkflowInstanceStore** に渡されます。

5. DP アプリケーションは SQL Workflow Instance Store を初期化し、 **promote** メソッドを呼び出してこのデータを昇格させます。

    ```csharp
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);

    List<XName> variantProperties = new List<XName>()
    {
        xNS.GetName("UserName"),
        xNS.GetName("ApprovalStatus"),
        xNS.GetName("DocumentId"),
        xNS.GetName("LastModifiedTime")
    };

    store.Promote("DocumentStatus", variantProperties, null);
    ```

    このプロモーション情報に基づいて、 **SqlWorkflowInstanceStore** は [InstancePromotedProperties](#InstancePromotedProperties) ビューの列にデータプロパティを配置します。

6. 昇格テーブルのデータのサブセットを照会するために、DP アプリケーションによって昇格ビューの上にカスタマイズされたビューが追加されます。

    ```sql
    create view [dbo].[DocumentStatus] with schemabinding
    as
        select  P.[InstanceId] as [InstanceId],
            P.Value1 as [UserName],
            P.Value2 as [ApprovalStatus],
            P.Value3 as [DocumentId],
            P.Value4 as [LastUpdatedTime]
    from [System.Activities.DurableInstancing].[InstancePromotedProperties] as P
    where P.PromotionName = N'DocumentStatus'
    go
    ```

## <a name="systemactivitiesdurableinstancinginstancepromotedproperties-view"></a><a name="InstancePromotedProperties"></a> [System.activities.durableinstancing.instances. InstancePromotedProperties] ビュー

|列名|列の型|説明|
|-----------------|-----------------|-----------------|
|InstanceId|GUID|この昇格が属するワークフロー インスタンス。|
|PromotionName|nvarchar(400)|昇格自体の名前。|
|Value1、Value2、Value3、…Value32|sql_variant|昇格したプロパティ自体の値。 ほとんどの SQL プリミティブ データ型はバイナリ ブロブを除外し、長さが 8,000 バイトを超える文字列は sql_variant に合わせて短縮されます。|
|Value33、Value34、Value35、…、Value64|varbinary(max)|varbinary(max) として明示的に宣言される昇格したプロパティの値。|
