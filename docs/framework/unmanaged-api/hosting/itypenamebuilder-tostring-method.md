---
description: '詳細情報: ITypeNameBuilder:: ToString メソッド'
title: ITypeNameBuilder::ToString メソッド
ms.date: 03/30/2017
api_name:
- ITypeNameBuilder.ToString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ToString
helpviewer_keywords:
- ToString method [.NET Framework hosting]
- ITypeNameBuilder::ToString method [.NET Framework hosting]
ms.assetid: 6372aca7-869a-4af6-ba2b-0eb1047ef5c0
topic_type:
- apiref
ms.openlocfilehash: 7caa6fd12fe8cbcebeaa19a7ae6da9931eacce8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680357"
---
# <a name="itypenamebuildertostring-method"></a>ITypeNameBuilder::ToString メソッド

このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ToString (  
    [out, retval] BSTR* pszStringRepresentation  
);  
```  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](hosting-interfaces.md)
