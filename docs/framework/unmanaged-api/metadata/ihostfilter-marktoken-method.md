---
description: '詳細について: IHostFilter:: MarkToken メソッド'
title: IHostFilter::MarkToken メソッド
ms.date: 03/30/2017
api_name:
- IHostFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type:
- apiref
ms.openlocfilehash: c8f5ecdef56b77e1b0031a93d6d8f7de79de4c3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784185"
---
# <a name="ihostfiltermarktoken-method"></a>IHostFilter::MarkToken メソッド

指定されたメタデータトークンが処理されることを示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `tk`  
 から処理するメタデータトークン。  
  
## <a name="remarks"></a>解説  

 通常、トークンがメタデータスコープ内にある場合は、トークンを処理する必要があります。 メソッドは、 `MarkToken` [IMetaDataEmit:: SetHandler](imetadataemit-sethandler-method.md) メソッドを使用してメタデータエンジンに渡されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ インターフェイス](metadata-interfaces.md)
- [IHostFilter インターフェイス](ihostfilter-interface.md)
