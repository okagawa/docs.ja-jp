---
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
ms.openlocfilehash: dfe247bda75c3695c7c09b85729b4e057c13c62d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95692632"
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
  
## <a name="remarks"></a>注釈  

 現在のバージョンのでは `ICorPublishProcess` 、マネージコードを持つプロセスのみにアクセスが許可されるため、は `IsManaged` 常にを返し `true` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorPub .idl、CorPub .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorPublishProcess インターフェイス](icorpublishprocess-interface.md)
