---
title: ワークフロー サービス内でのシリアル化の構成
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: d1cda33c8a469b4a54b6d282b99c07b23e91543e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96284200"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>ワークフロー サービス内でのシリアル化の構成

ワークフローサービスは Windows Communication Foundation (WCF) サービスであるため、 <xref:System.Runtime.Serialization.DataContractSerializer> (既定値) またはを使用することも <xref:System.Xml.Serialization.XmlSerializer> できます。 ワークフロー以外のサービスを記述する場合、使用するシリアライザーの型はサービスまたは操作コントラクトで指定されます。 WCF ワークフローサービスを作成する場合、これらのコントラクトはコードで指定せずに、コントラクト推論によって実行時に生成されます。 コントラクト推論の詳細については、「  [ワークフローでのコントラクトの使用](using-contracts-in-workflow.md)」を参照してください。  シリアライザーは、<xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> プロパティを使用して指定されます。 これは、次の図に示すようにデザイナーで設定できます。  
  
 ![[プロパティ] ウィンドウで SerializerOption プロパティを設定します。](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 シリアライザーは、次の例に示すようにコードで設定することもできます。  
  
```csharp  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
  ワークフロー サービスにも既知の型を指定できます。 既知の型の詳細については、「 [データコントラクトの既知の型](data-contract-known-types.md)」を参照してください。 既知の型は、デザイナーまたはコードで指定できます。 デザイナーで既知の型を指定するには、次の図に示すように、アクティビティの [ **プロパティ] ウィンドウ** で knowntypes プロパティの横にある省略記号ボタンをクリックし <xref:System.ServiceModel.Activities.Receive> ます。
  
 ![KnownTypes プロパティダイアログボックスのスクリーンショット。](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 これにより、既知の型を検索して指定するための型コレクションエディターが表示されます。  
  
 ![型コレクションエディターのスクリーンショット。](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 [ **新しい型の追加** ] リンクをクリックし、ドロップダウンを使用して、既知の型のコレクションに追加する型を選択または検索します。 既知の型をコードで指定するには、次の例に示すように <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> プロパティを使用します。  
  
```csharp
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
            approveExpense.KnownTypes.Add(typeof(Travel));  
            approveExpense.KnownTypes.Add(typeof(Meal));  
```
