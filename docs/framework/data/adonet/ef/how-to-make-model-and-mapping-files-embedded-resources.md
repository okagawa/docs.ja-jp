---
description: '詳細情報: 方法:モデル ファイルとマッピング ファイルを組み込みリソースにする'
title: '方法: モデル ファイルとマッピング ファイルを組み込みリソースにする'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 373dfc2c93adfc510341ec0ea0487ad8962aa3e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697518"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>方法: モデル ファイルとマッピング ファイルを組み込みリソースにする

Entity Framework を使用すると、モデル ファイルとマッピング ファイルをアプリケーションの組み込みリソースとして配置できます。 モデル ファイルとマッピング ファイルが組み込まれたアセンブリは、エンティティ接続と同じアプリケーション ドメインに読み込む必要があります。 詳細については、「[Connection Strings (接続文字列)](connection-strings.md)」をご覧ください。 既定では、Entity Data Model ツールによって、モデル ファイルとマッピング ファイルが組み込まれます。 モデル ファイルとマッピング ファイルを手動で定義する場合は、Entity Framework アプリケーションと共にモデル ファイルとマッピング ファイルが組み込みリソースとして確実に配置されるように、この手順を使用します。  
  
> [!NOTE]
> 組み込みリソースを保持するには、モデル ファイルとマッピング ファイルを変更するたびに、この手順を繰り返す必要があります。  
  
### <a name="to-embed-model-and-mapping-files"></a>モデル ファイルとマッピング ファイルを組み込むには  
  
1. **ソリューション エクスプローラー** で、概念 (.csdl) ファイルを選択します。  
  
2. **[プロパティ]** ペインで、 **[ビルド アクション]** を **[組み込まれたリソース]** に設定します。  
  
3. ストレージ (.ssdl) ファイルとマッピング (.msl) ファイルに対して手順 1. と手順 2. を繰り返します。  
  
4. **ソリューション エクスプローラー** で、App.config ファイルをダブルクリックし、次のいずれかの形式に基づいて `connectionString` 属性の `Metadata` パラメーターを変更します。  
  
    - `Metadata=` `res://<assemblyFullName>/<resourceName>;`  
  
    - `Metadata=` `res://*/<resourceName>;`  
  
    - `Metadata=res://*;`  
  
     詳細については、「[Connection Strings (接続文字列)](connection-strings.md)」をご覧ください。  
  
## <a name="example"></a>例  

 次の接続文字列では、[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) の組み込みモデル ファイルとマッピング ファイルが参照されます。 この接続文字列は、プロジェクトの App.config ファイルに格納されています。  

## <a name="see-also"></a>関連項目

- [モデリングとマッピング](modeling-and-mapping.md)
- [方法: 接続文字列を定義する](how-to-define-the-connection-string.md)
- [方法: EntityConnection の接続文字列を作成する](how-to-build-an-entityconnection-connection-string.md)
- [ADO.NET Entity Data Model ツール](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
