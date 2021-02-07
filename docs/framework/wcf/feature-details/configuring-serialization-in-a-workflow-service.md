---
description: 詳細については、「ワークフローサービスでのシリアル化の構成」を参照してください。
title: ワークフロー サービス内でのシリアル化の構成
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: e268f82fc3c1f65086e3c6b112e481ad8abed070
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743240"
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
