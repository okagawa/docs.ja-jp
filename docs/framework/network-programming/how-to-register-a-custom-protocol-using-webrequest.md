---
description: '詳細情報: 方法:WebRequest を使用してカスタム プロトコルを登録する'
title: '方法: WebRequest を使用してカスタム プロトコルを登録する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 7415017f20c0c6ed80570992e249fb8121907de2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785758"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a>方法: WebRequest を使用してカスタム プロトコルを登録する

この例では、他の場所で定義されているプロトコル固有のクラスを登録する方法を示します。 この例では、`CustomWebRequestCreator` は、`CustomWebRequest` オブジェクトを返す **Create** メソッドを実装するユーザー実装のオブジェクトです。 このコード例では、カスタム プロトコルを実装する `CustomWebRequest` コードが既に作成されているものとします。  
  
## <a name="example"></a>例  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  

 この例で必要な要素は次のとおりです。  
  
 <xref:System.Net> 名前空間への参照。  
  
## <a name="see-also"></a>関連項目

- [プラグ可能なプロトコルのプログラミング](programming-pluggable-protocols.md)
