---
description: '詳細情報: 方法:エンティティをシリアル化可能にする'
title: '方法: エンティティをシリアル化可能にする'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: cb2253d7933f3584543b4b030bc8b5aa3cc62921
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785940"
---
# <a name="how-to-make-entities-serializable"></a>方法: エンティティをシリアル化可能にする

コードを作成するときに、エンティティをシリアル化可能にできます。 エンティティ クラスは <xref:System.Runtime.Serialization.DataContractAttribute> 属性で装飾し、列は <xref:System.Runtime.Serialization.DataMemberAttribute> 属性で装飾します。  
  
 Visual Studio を使用している開発者は、オブジェクト リレーショナル デザイナーをこの目的に使用できます。  
  
 SQLMetal コマンド ライン ツールを使用する場合は、`unidirectional` 引数を指定して **/serialization** オプションを使用します。 詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。  
  
## <a name="example"></a>例  

 次の SQLMetal コマンド ラインでは、シリアル化可能なエンティティを持つファイルが作成されます。  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a>関連項目

- [シリアル化](serialization.md)
- [オブジェクト モデルの作成](creating-the-object-model.md)
