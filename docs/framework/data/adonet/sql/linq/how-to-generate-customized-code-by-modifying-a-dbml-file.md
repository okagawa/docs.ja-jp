---
description: '詳細情報: 方法:DBML ファイルを変更してカスタマイズ コードを生成する'
title: '方法: DBML ファイルを変更してカスタマイズ コードを生成する'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 0dd4024b3f6a0ca0583de6bfbdb7463fab14d969
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786005"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>方法: DBML ファイルを変更してカスタマイズ コードを生成する

データベース マークアップ言語 (.dbml) のメタデータ ファイルから、Visual Basic または C# のソース コードを生成できます。 この方法を使用すると、アプリケーション マッピング コードを生成する前に、既定の .dbml ファイルをカスタマイズできます。 これは高度な機能です。  
  
 実行手順は次のとおりです。  
  
1. .dbml ファイルを生成します。  
  
2. エディターを使用して .dbml ファイルを変更します。 .dbml ファイルは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の .dbml ファイルのスキーマ定義 (.xsd) ファイルに対して有効である必要があることに注意してください。 詳しくは、「[LINQ to SQL でのコード生成](code-generation-in-linq-to-sql.md)」をご覧ください。  
  
3. Visual Basic または C# のソース コードを生成します。  
  
 次の例では、SQLMetal コマンド ライン ツールを使用します。 詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。  
  
## <a name="example"></a>例  

 次のコードでは、Northwind サンプル データベースから .dbml ファイルを生成します。 データベース メタデータのソースとして、データベースの名前または .mdf ファイルの名前を使用します。  
  
```console  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>例  

 次のコードでは、.dbml ファイルから Visual Basic または C# のソース コードが生成されます。  
  
```console
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>関連項目

- [LINQ to SQL でのコード生成](code-generation-in-linq-to-sql.md)
- [SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [オブジェクト モデルの作成](creating-the-object-model.md)
