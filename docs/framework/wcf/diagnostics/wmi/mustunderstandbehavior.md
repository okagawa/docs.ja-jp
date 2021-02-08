---
description: '詳細情報: 実行時の動作'
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 173548f2f3346a79bf7f53c90384db94a638a366
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803127"
---
# <a name="mustunderstandbehavior"></a>MustUnderstandBehavior

MustUnderstandBehavior  
  
## <a name="syntax"></a>構文  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>メソッド  

 MustUnderstandBehavior クラスで定義されるメソッドはありません。  
  
## <a name="properties"></a>プロパティ  

 MustUnderstandBehavior クラスには、次のプロパティがあります。  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 `true` の場合、未処理の `MustUnderstand` 属性を持つすべての SOAP ヘッダーは、動作が例外をスローする原因となります。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>
