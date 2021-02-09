---
description: '詳細情報: 継承のサポート'
title: 継承のサポート
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: ff6956441ab72f720151e42bd9358c8df1170e09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803868"
---
# <a name="inheritance-support"></a>継承のサポート

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、"*シングル テーブル マッピング*" がサポートされます。 これは、1 つの継承階層全体が単一のデータベース テーブルに保存されることを意味します。 テーブルには、階層構造内で使用され得るすべてのデータ列の平坦化された共用体が格納されます  (2 つのテーブルを 1 つに結合し、元のテーブルのいずれかにあった行が新しいテーブルに含まれるようにした結果、1 つの共用体が形成されます)。行によって表されるインスタンスの型に適合しない列には null が設定されます。  
  
 シングル テーブル マッピング形式は、継承を表す最も単純な形式であり、多くのクエリのカテゴリで良好なパフォーマンス特性を示します。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] でこのマッピングを実装するには、継承階層のルート クラスで属性および属性プロパティを指定する必要があります。 詳細については、[継承階層を割り当てる](how-to-map-inheritance-hierarchies.md)」を参照してください。  
  
 Visual Studio を使用している開発者は、オブジェクト リレーショナル デザイナーを使用して継承改装をマップすることもできます。  
  
## <a name="see-also"></a>関連項目

- [背景情報](background-information.md)
