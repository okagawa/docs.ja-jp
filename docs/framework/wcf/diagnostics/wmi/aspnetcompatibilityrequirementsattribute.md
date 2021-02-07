---
description: '詳細情報: AspNetCompatibilityRequirementsAttribute'
title: AspNetCompatibilityRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 00908a39-a21b-4029-bbb9-33e5a6ed25a7
ms.openlocfilehash: 9b4b28a018b441edfc744835e61d2a9413f35302
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757957"
---
# <a name="aspnetcompatibilityrequirementsattribute"></a>AspNetCompatibilityRequirementsAttribute

AspNetCompatibilityRequirementsAttribute  
  
## <a name="syntax"></a>構文  
  
```csharp
class AspNetCompatibilityRequirementsAttribute : Behavior  
{  
  string RequirementsMode;  
};  
```  
  
## <a name="methods"></a>メソッド  

 AspNetCompatibilityRequirementsAttribute クラスは、メソッドをすべて定義しません。  
  
## <a name="properties"></a>プロパティ  

 AspNetCompatibilityRequirementsAttribute クラスには、次のプロパティがあります。  
  
### <a name="requirementsmode"></a>RequirementsMode  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 ASP.NET 互換モードがアクティブかどうかを示します。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.ServiceHostingEnvironment.AspNetCompatibilityEnabled%2A>
