---
description: '詳細については、「方法: Request-Reply コントラクトを作成する」を参照してください。'
title: '方法: 要求/応答コントラクトを作成する'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: f5e63538a405aa451ffd3be114485604c00fa407
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734699"
---
# <a name="how-to-create-a-request-reply-contract"></a>方法: 要求/応答コントラクトを作成する

要求/応答コントラクトは、応答を返すメソッドを指定します。 応答が送信され、このコントラクトの条件の下で要求に関連付けられる必要があります。 メソッドが応答を返さない場合 (C# の場合は `void` または Visual Basic の場合は `Sub`) でも、インフラストラクチャは、空のメッセージを作成して送信することで、メソッドが返ったことを呼び出し元に示します。 空の応答メッセージが送信されるのを防ぐには、操作で 1 方向コントラクトを使用します。  
  
### <a name="to-create-a-request-reply-contract"></a>要求/応答コントラクトを作成するには  
  
1. 選択したプログラミング言語でインターフェイスを作成します。  
  
2. インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> 属性を適用します。  
  
3. クライアントが呼び出すことのできる各メソッドに <xref:System.ServiceModel.OperationContractAttribute> 属性を適用します。  
  
4. 任意。 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> プロパティの値を `true` に設定して、空の応答メッセージが送信されることを防止します。 既定では、すべての操作は要求/応答コントラクトです。  
  
## <a name="example"></a>例  

 次のサンプルは、`Add` メソッドと `Subtract` メソッドを提供する電卓サービスのコントラクトを定義します。 `Multiply` メソッドは <xref:System.ServiceModel.OperationContractAttribute> クラスでマークされていないため、このコントラクトの一部ではありません。したがって、クライアントからはアクセスできません。  
  
```csharp
using System.ServiceModel;

[ServiceContract]
public interface ICalculator
{
    [OperationContract]
    // It would be equivalent to write explicitly:
    // [OperationContract(IsOneWay=false)]
    int Add(int a, int b);

    [OperationContract]
    int Subtract(int a, int b);

    int Multiply(int a, int b)
}
```
  
- 操作コントラクトを指定する方法の詳細については、 <xref:System.ServiceModel.OperationContractAttribute> クラスとプロパティを参照してください <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 。  
  
- <xref:System.ServiceModel.ServiceContractAttribute> 属性と <xref:System.ServiceModel.OperationContractAttribute> 属性を適用すると、サービスを展開した後に Web サービス記述言語 (WSDL) ドキュメントでサービス コントラクト定義が自動的に生成されます。 ドキュメントは、サービスの HTTP ベース アドレスに `?wsdl` を付け加えてしてダウンロードできます。 たとえば、`http://microsoft/CalculatorService?wsdl`  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.OperationContractAttribute>
- [サービス コントラクトの設計](../designing-service-contracts.md)
- [方法: 双方向コントラクトを作成する](how-to-create-a-duplex-contract.md)
