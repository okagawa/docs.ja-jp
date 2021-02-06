---
description: '詳細について: IMetaDataEmit:: SetHandler メソッド'
title: IMetaDataEmit::SetHandler メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
ms.openlocfilehash: 07ebf8eef816d373e92a82fc84adacfe5a8599fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657868"
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler メソッド

指定したポインターによって参照されるメソッドを、 `IUnknown` トークンリマップの通知コールバックとして設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pUnk`  
 から登録するハンドラー。  
  
## <a name="remarks"></a>解説  

 メタデータエンジンは、によって提供されるメソッドを使用して、最適化された `SetHandler` 方法でレコードを生成せず、保存されたレコードを最適化するコンパイラに通知を送信します。  
  
 コールバックメソッドがによって提供されていない場合 `SetHandler` 、 `IMapToken` 各スコープに対して merge on merge を使用して複数のインポートスコープがマージされている場合を除き、保存時に最適化は実行されません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](imetadataemit2-interface.md)
