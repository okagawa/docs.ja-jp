---
description: '詳細情報: 方法:Visual Basic または C# でオブジェクト モデルを生成する'
title: '方法: Visual Basic または C# でオブジェクト モデルを生成する'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: d842a646f9f6186d252d10297618ddc2cb137e70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785966"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>方法: Visual Basic または C\# でオブジェクト モデルを生成する

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、使用しているプログラミング言語のオブジェクト モデルが、リレーショナル データベースに対応付けられています。 既存のデータベースのメタデータから Visual Basic または C# のモデルを自動的に生成するには、2 つのツールを使用できます。  
  
- Visual Studio を使用している場合は、オブジェクト リレーショナル デザイナーを使用して、オブジェクト モデルを生成できます。 O/R デザイナーでは、機能が豊富なユーザー インターフェイスを使用して、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のオブジェクト モデルを生成できます。 詳しくは、「[Visual Studio の LINQ to SQL ツール](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)」をご覧ください。
  
- SQLMetal コマンド ライン ツール。 詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。  
  
    > [!NOTE]
    > 既存のデータベースがなく、オブジェクト モデルからデータベースを作成する場合は、コード エディターと <xref:System.Data.Linq.DataContext.CreateDatabase%2A> を使用してオブジェクト モデルを作成できます。 詳細については、[データベースを動的に作成する](how-to-dynamically-create-a-database.md)」を参照してください。  
  
 O/R デザイナーのドキュメントでは、O/R デザイナーを使用して Visual Basic または C# のオブジェクト モデルを生成する方法の例が提供されています。 以下の情報は、SQLMetal コマンド ライン ツールの使用方法の例です。 詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。  
  
## <a name="example"></a>例  

 次の例に示す SQLMetal のコマンド ラインでは、Northwind サンプル データベースの属性ベースのオブジェクト モデルとして Visual Basic のコードが生成されます。 ストアド プロシージャと関数も含まれます。  
  
```console  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>例  

 次の例に示す SQLMetal コマンド ラインでは、Northwind サンプル データベースの属性ベースのオブジェクト モデルとして C# コードが生成されます。 ストアド プロシージャと関数も含まれ、テーブル名は自動的に複数化されます。  
  
```console  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>関連項目

- [プログラミング ガイド](programming-guide.md)
- [LINQ to SQL オブジェクト モデル](the-linq-to-sql-object-model.md)
- [チュートリアルによる学習](learning-by-walkthroughs.md)
- [方法: コード エディターを使用してエンティティ クラスをカスタマイズする](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [属性ベースの対応付け](attribute-based-mapping.md)
- [SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [外部マップ](external-mapping.md)
- [サンプル データベースのダウンロード](downloading-sample-databases.md)
- [オブジェクト モデルの作成](creating-the-object-model.md)
