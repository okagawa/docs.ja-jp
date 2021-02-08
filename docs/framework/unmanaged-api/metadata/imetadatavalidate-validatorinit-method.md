---
description: '詳細について: IMetaDataValidate:: ValidatorInit メソッド'
title: IMetaDataValidate::ValidatorInit メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataValidate.ValidatorInit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataValidate::ValidatorInit
helpviewer_keywords:
- IMetaDataValidate::ValidatorInit method [.NET Framework metadata]
- ValidatorInit method [.NET Framework metadata]
ms.assetid: 6bafd75a-e2d0-4aea-aed1-074374d5dff6
topic_type:
- apiref
ms.openlocfilehash: 99435eeab542e9cb3bb679ad146b546ce51c8df4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799188"
---
# <a name="imetadatavalidatevalidatorinit-method"></a>IMetaDataValidate::ValidatorInit メソッド

現在のメタデータ スコープ内にあるモジュールの種類を指定するフラグを設定し、指定されたコールバック メソッドを検証エラー用に登録します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `dwModule`  
 から現在のメタデータスコープ内のモジュールの型を指定する [Corvalidatormoduletype](corvalidatormoduletype-enumeration.md) 列挙体の値。  
  
 `pUnk`  
 から検証エラーの関数コールバックとして機能する [IUnknown](/cpp/atl/iunknown) インスタンスへのポインター。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataValidate インターフェイス](imetadatavalidate-interface.md)
