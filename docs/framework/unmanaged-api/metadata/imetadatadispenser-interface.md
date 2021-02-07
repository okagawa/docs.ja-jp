---
description: 詳細については、「IMetaDataDispenser インターフェイス」を参照してください。
title: IMetaDataDispenser インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser
helpviewer_keywords:
- IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type:
- apiref
ms.openlocfilehash: 5ba37fc05a4e1897b100967d32b268f91a0e4402
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721009"
---
# <a name="imetadatadispenser-interface"></a>IMetaDataDispenser インターフェイス

新しいメタデータスコープを作成したり、既存のメタデータスコープを開いたりするためのメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[DefineScope メソッド](imetadatadispenser-definescope-method.md)|新しいメタデータを作成できる新しい領域をメモリに作成します。|  
|[OpenScope メソッド](imetadatadispenser-openscope-method.md)|ディスク上の既存のファイルを開き、そのメタデータをメモリにマップします。|  
|[OpenScopeOnMemory メソッド](imetadatadispenser-openscopeonmemory-method.md)|既存のメタデータを含むメモリ領域を開きます。 つまり、このメソッドは、既存のデータがメタデータとして扱われる、指定されたメモリ領域を開きます。|  
  
## <a name="requirements"></a>要件  

 **プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataDispenserEx インターフェイス](imetadatadispenserex-interface.md)
- [メタデータ インターフェイス](metadata-interfaces.md)
