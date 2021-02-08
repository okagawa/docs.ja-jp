---
description: 詳細については、「コントラクトの最初のワークフローサービスの開発」を参照してください。
title: コントラクト優先ワークフロー サービスの開発
ms.date: 03/30/2017
ms.assetid: e5dbaa7b-005f-4330-848d-58ac4f42f093
ms.openlocfilehash: 54f6c0c5de45187bd65e45d22978e6e9b105f3e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792714"
---
# <a name="contract-first-workflow-service-development"></a>コントラクト優先ワークフロー サービスの開発

.NET Framework 4.5 以降、Windows Workflow Foundation (WF) 機能により、コントラクト優先のワークフロー開発という形で、web サービスとワークフローの統合が向上しています。 コントラクト優先ワークフローの開発ツールでは、コードのコントラクトを先に設計できます。 その後、ツールボックス内に、コントラクト内の操作用のアクティビティ テンプレートが自動的に生成されます。 このトピックでは、ワークフロー サービスのアクティビティおよびプロパティをサービス コントラクトの属性にマップする方法の概要について説明します。 コントラクト優先ワークフローサービスを作成する手順の例については、「 [方法: 既存のサービスコントラクトを使用するワークフローサービスを作成](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)する」を参照してください。

## <a name="in-this-topic"></a>このトピックの内容

- [ワークフロー属性へのサービス コントラクト属性のマップ](contract-first-workflow-service-development.md#MappingAttributes)

  - [サービス コントラクト属性](contract-first-workflow-service-development.md#ServiceContract)

  - [操作コントラクト属性](contract-first-workflow-service-development.md#OperationContract)

  - [メッセージ コントラクト属性](contract-first-workflow-service-development.md#MessageContract)

  - [データ コントラクト属性](contract-first-workflow-service-development.md#DataContract)

  - [エラー コントラクト属性](contract-first-workflow-service-development.md#FaultContract)

- [サポートおよび実装に関する詳細情報](contract-first-workflow-service-development.md#AdditionalSupport)

  - [サポートされていないサービス コントラクト機能](contract-first-workflow-service-development.md#UnsupportedFeatures)

  - [構成済みのメッセージング アクティビティの生成](contract-first-workflow-service-development.md#ActivityGeneration)

## <a name="mapping-service-contract-attributes-to-workflow-attributes"></a><a name="MappingAttributes"></a> ワークフロー属性へのサービスコントラクト属性のマッピング

次のセクションにある表では、さまざまな WCF 属性およびプロパティを示し、それらをコントラクト優先ワークフローのメッセージング アクティビティおよびプロパティにマップする方法について説明します。

- [サービス コントラクト属性](contract-first-workflow-service-development.md#ServiceContract)

- [操作コントラクト属性](contract-first-workflow-service-development.md#OperationContract)

- [メッセージ コントラクト属性](contract-first-workflow-service-development.md#MessageContract)

- [データ コントラクト属性](contract-first-workflow-service-development.md#DataContract)

- [エラー コントラクト属性](contract-first-workflow-service-development.md#FaultContract)

### <a name="service-contract-attributes"></a><a name="ServiceContract"></a> サービスコントラクト属性

|プロパティ名|サポートされています|説明|WF の検証|
|-------------------|---------------|-----------------|-------------------|
|CallbackContract|いいえ|コントラクトが双方向コントラクトの場合のコールバック コントラクトの型を取得または設定します。|(なし)|
|ConfigurationName|いいえ|アプリケーション構成ファイル内でサービスを検索するために使用される名前を取得または設定します。|(なし)|
|HasProtectionLevel|はい|メンバーに保護レベルが割り当てられているかどうかを示す値を取得します。|Receive.ProtectionLevel を null にすることはできません。|
|名前|はい|Web サービス記述言語 (WSDL) での \<portType> 要素の名前を取得または設定します。|Receive.ServiceContractName.LocalName が一致している必要があります。|
|名前空間|はい|Web サービス記述言語 (WSDL) での \<portType> 要素の名前空間を取得または設定します。|Receive.ServiceContractName.NameSpace が一致している必要があります。|
|ProtectionLevel|はい|コントラクトのバインドで、ProtectionLevel プロパティの値をサポートする必要があるかどうかを指定します。|Receive.ProtectionLevel が一致している必要があります。|
|SessionMode|いいえ|セッションが許可されるか、許可されないか、または必要であるかを示す値を取得または設定します。|(なし)|
|TypeId|いいえ|派生クラスに実装した場合、この属性の一意の識別子を取得します。 (属性から継承)。|(なし)|

ここにサブセクション本文を挿入。

### <a name="operation-contract-attributes"></a><a name="OperationContract"></a> 操作コントラクト属性

|プロパティ名|サポートされています|説明|WF の検証|
|-------------------|---------------|-----------------|-------------------|
|アクション|はい|要求メッセージの WS-Addressing アクションを取得または設定します。|Receive.Action が一致している必要があります。|
|AsyncPattern|いいえ|\<methodName>サービスコントラクトで Begin および End メソッドのペアを使用して、操作が非同期的に実装されることを示し \<methodName> ます。|(なし)|
|HasProtectionLevel|はい|この操作のメッセージの暗号化、署名、または両方が必要かどうかを示す値を取得または設定します。|Receive.ProtectionLevel を null にすることはできません。|
|IsInitiating|いいえ|メソッドが (セッションが存在する場合に) サーバー上でセッションを開始できる操作を実装するかどうかを示す値を取得または設定します。|(なし)|
|IsOneWay|はい|操作が応答メッセージを返すかどうかを示す値を取得または設定します。|(この Receive の SendReply またはこの Send の ReceiveReply がありません。)|
|IsTerminating|いいえ|応答メッセージが存在する場合に、そのメッセージの送信後にセッションを終了するようにサービス操作がサーバーに指示するかどうかを示す値を取得または設定します。|(なし)|
|名前|はい|操作の名前を取得します。値の設定も可能です。|Receive.OperationName が一致している必要があります。|
|ProtectionLevel|はい|操作のメッセージの暗号化、署名、または両方が必要かどうかを示す値を取得または設定します。|Receive.ProtectionLevel が一致している必要があります。|
|ReplyAction|はい|操作の応答メッセージの SOAP アクションの値を取得または設定します。|SendReply.Action が一致している必要があります。|
|TypeId|いいえ|派生クラスに実装した場合、この属性の一意の識別子を取得します。 (属性から継承)。|(なし)|

### <a name="message-contract-attributes"></a><a name="MessageContract"></a> メッセージコントラクト属性

|プロパティ名|サポートされています|説明|WF の検証|
|-------------------|---------------|-----------------|-------------------|
|HasProtectionLevel|はい|メッセージに保護レベルが割り当てられているかどうかを示す値を取得します。|検証なし (Receive.Content と SendReply.Content がメッセージ コントラクト型と一致している必要があります)。|
|IsWrapped|はい|メッセージ本文にラッパー要素があるかどうかを指定する値を取得または設定します。|検証なし (Receive.Content と Sendreply.Content がメッセージ コントラクト型と一致している必要があります)。|
|ProtectionLevel|いいえ|メッセージの暗号化、署名、または両方が必要かどうかを指定する値を取得または設定します。|(なし)|
|TypeId|はい|派生クラスに実装した場合、この属性の一意の識別子を取得します。 (属性から継承)。|検証なし (Receive.Content と SendReply.Content がメッセージ コントラクト型と一致している必要があります)。|
|WrapperName|はい|メッセージ本文のラッパー要素の名前を取得または設定します。|検証なし (Receive.Content と SendReply.Content がメッセージ コントラクト型と一致している必要があります)。|
|WrapperNamespace|いいえ|メッセージ本文のラッパー要素の名前空間を取得または設定します。|(なし)|

### <a name="data-contract-attributes"></a><a name="DataContract"></a> データコントラクト属性

|プロパティ名|サポートされています|説明|WF の検証|
|-------------------|---------------|-----------------|-------------------|
|IsReference|いいえ|オブジェクト参照データを保持するかどうかを示す値を取得または設定します。|(なし)|
|名前|はい|型のデータ コントラクトの名前を取得または設定します。|検証なし (Receive.Content と SendReply.Content がメッセージ コントラクト型と一致している必要があります)。|
|名前空間|はい|型のデータ コントラクトの名前空間を取得または設定します。|検証なし (Receive.Content と SendReply.Content がメッセージ コントラクト型と一致している必要があります)。|
|TypeId|いいえ|派生クラスに実装した場合、この属性の一意の識別子を取得します。 (属性から継承)。|(なし)|

### <a name="fault-contract-attributes"></a><a name="FaultContract"></a> エラーコントラクト属性

|プロパティ名|サポートされています|説明|WF の検証|
|-------------------|---------------|-----------------|-------------------|
|アクション|はい|操作コントラクトの一部として指定された SOAP エラー メッセージのアクションを取得または設定します。|SendReply.Action が一致している必要があります。|
|DetailType|はい|エラー情報を含むシリアル化可能なオブジェクトの型を取得します。|SendReply.Content が型と一致している必要があります。|
|HasProtectionLevel|いいえ|SOAP エラー メッセージに保護レベルが割り当てられているかどうかを示す値を取得します。|(なし)|
|名前|いいえ|Web サービス記述言語 (WSDL) でのエラー メッセージの名前を取得または設定します。|(なし)|
|名前空間|いいえ|SOAP エラーの名前空間を取得または設定します。|(なし)|
|ProtectionLevel|いいえ|SOAP エラーがバインドに要求する保護レベルを指定します。|(なし)|
|TypeId|いいえ|派生クラスに実装した場合、この属性の一意の識別子を取得します。 (属性から継承)。|(なし)|

## <a name="additional-support-and-implementation-information"></a><a name="AdditionalSupport"></a> 追加のサポートと実装に関する情報

- [サポートされていないサービス コントラクト機能](contract-first-workflow-service-development.md#UnsupportedFeatures)

- [構成済みのメッセージング アクティビティの生成](contract-first-workflow-service-development.md#ActivityGeneration)

### <a name="unsupported-service-contract-features"></a><a name="UnsupportedFeatures"></a> サポートされていないサービスコントラクト機能

- コントラクトでの TPL (タスク並列ライブラリ) タスクの使用はサポートされていません。

- サービス コントラクトの継承はサポートされていません。

### <a name="generation-of-configured-messaging-activities"></a><a name="ActivityGeneration"></a> 構成済みメッセージングアクティビティの生成

コントラクト優先ワークフロー サービスを使用する場合に事前構成されたメッセージ アクティビティの生成をサポートするために、2 つのパブリック静的メソッドが <xref:System.ServiceModel.Activities.Receive> アクティビティと <xref:System.ServiceModel.Activities.SendReply> アクティビティに追加されています。

- <xref:System.ServiceModel.Activities.Receive.FromOperationDescription%2A?displayProperty=nameWithType>

- <xref:System.ServiceModel.Activities.SendReply.FromOperationDescription%2A?displayProperty=nameWithType>

これらのメソッドによって生成されたアクティビティはコントラクト検証に合格する必要があるため、これらのメソッドは <xref:System.ServiceModel.Activities.Receive> および <xref:System.ServiceModel.Activities.SendReply> の検証ロジックの一部として内部で使用されます。 <xref:System.ServiceModel.Activities.Receive.OperationName%2A>、<xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>、<xref:System.ServiceModel.Activities.Receive.Action%2A>、<xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>、<xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A>、および <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> はすべて、インポートされたコントラクトに一致するよう事前に構成されています。 ワークフローデザイナーのアクティビティの [コンテンツのプロパティ] ページでは、 **メッセージ** または **パラメーター** のセクションもコントラクトと一致するように事前に構成されています。

WCF エラーコントラクトは <xref:System.ServiceModel.Activities.SendReply> 、に表示される各エラーに対して、構成済みの個別のアクティビティセットを返すことによっても処理され <xref:System.ServiceModel.Description.OperationDescription.Faults%2A> <xref:System.ServiceModel.Description.FaultDescriptionCollection> ます。

<xref:System.ServiceModel.Description.OperationDescription>現在、WF サービスでサポートされていないのその他の部分 (WebGet/WebInvoke の動作、カスタム動作の動作など) については、API は生成と構成の一部としてこれらの値を無視します。 例外はスローされません。
