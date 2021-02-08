---
description: '詳細について: ICorPublishProcess:: IsManaged メソッド'
title: ICorPublishProcess::IsManaged メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
ms.openlocfilehash: 55f620a896efd87c2f154ac68ef2db1a1b0a1ebc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790504"
---
# <a name="icorpublishprocessismanaged-method"></a>ICorPublishProcess::IsManaged メソッド

この [ICorPublishProcess](icorpublishprocess-interface.md) によって参照されるプロセスに、マネージコードがあることがわかっているかどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pbManaged`  
 入出力プロセスにマネージコードがあるかどうかを示すブール値へのポインター。 `true`プロセスにマネージコードがある場合は、値はです。それ以外の場合は `false` です。  
  
## <a name="remarks"></a>解説  

 現在のバージョンのでは `ICorPublishProcess` 、マネージコードを持つプロセスのみにアクセスが許可されるため、は `IsManaged` 常にを返し `true` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorPub .idl、CorPub .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorPublishProcess インターフェイス](icorpublishprocess-interface.md)
