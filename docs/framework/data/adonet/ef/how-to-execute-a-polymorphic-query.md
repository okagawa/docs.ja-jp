---
description: '詳細情報: 方法:ポリモーフィック クエリを実行する'
title: '方法: ポリモーフィック クエリを実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: 02074fb0ad60e5ba8d62094e25f35db40f8a2dbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650732"
---
# <a name="how-to-execute-a-polymorphic-query"></a>方法: ポリモーフィック クエリを実行する

このトピックでは、[OFTYPE](./language-reference/oftype-entity-sql.md) 演算子を使ってポリモーフィックな [!INCLUDE[esql](../../../../../includes/esql-md.md)] クエリを実行する方法について説明します。

### <a name="to-run-the-code-in-this-example"></a>この例のコードを実行するには

1. [School モデル](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))をプロジェクトに追加し、Entity Framework が使用されるようにプロジェクトを構成します。 詳細については、[Entity Data Model ウィザードを使用する](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))」を参照してください。

2. アプリケーションのコード ページで、次の `using` ステートメント (Visual Basic の場合は `Imports`) を追加します。

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. 概念モデルを変更して、Table-Per-Hierarchy 継承を持つようにします。そのためには、「[チュートリアル:Table-Per-Hierarchy 継承のマッピング](/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100))」で説明されている手順に従います。

## <a name="example"></a>例

次の例では、OFTYPE 演算子を使用し、`OnsiteCourses` のコレクションから `Courses` のコレクションだけを取得して表示します。

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a>関連項目

- [Entity Framework 用の EntityClient プロバイダー](entityclient-provider-for-the-entity-framework.md)
- [Entity SQL 言語](./language-reference/entity-sql-language.md)
