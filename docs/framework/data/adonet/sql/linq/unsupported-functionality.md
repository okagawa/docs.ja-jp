---
description: '詳細情報: サポートされていない機能'
title: サポートされていない機能
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: 5c44dd4aad2d2ee4ec5e00ce42f4de9400cea478
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680890"
---
# <a name="unsupported-functionality"></a>サポートされていない機能

LINQ to SQL では、次の SQL 機能は、既存の共通言語ランタイム (CLR) および .NET Framework の構成要素の変換からは公開できません。  
  
- `STDDEV`  
  
- `LIKE`  
  
     `LIKE` は直接変換によってサポートされませんが、同様の機能が <xref:System.Data.Linq.SqlClient.SqlMethods> クラスにあります。 詳細については、「<xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>」を参照してください。  
  
- `DATEDIFF`  
  
     LINQ to SQL では、`DATEDIFF` のサポートが制限されています。 同様の機能が <xref:System.Data.Linq.SqlClient.SqlMethods> クラスにあります。  
  
- `ROUND`  
  
     LINQ to SQL では、`ROUND` のサポートが制限されています。 詳細については、「[System.Math メソッド](system-math-methods.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [データ型と関数](data-types-and-functions.md)
