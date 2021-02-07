---
description: '詳細情報: ヘルプモジュール:: GetMetaDataInterface メソッド'
title: ICorDebugModule::GetMetaDataInterface メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
ms.openlocfilehash: 39af2560b4c10f6dc490bfba5425e2339a7c1823
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691641"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a>ICorDebugModule::GetMetaDataInterface メソッド

モジュールのメタデータを調べるために使用できるメタデータインターフェイスオブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `riid`  
 からメタデータインターフェイスを指定する参照 ID。  
  
 `ppObj`  
 入出力`T:IUnknown`[メタデータインターフェイス](../metadata/metadata-interfaces.md)の1つであるオブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 デバッガーは、メソッドを使用して `GetMetaDataInterface` モジュールの元のメタデータのコピーを作成できます。モジュールは、モジュールを編集するために実行する必要があります。 デバッガーはを呼び出して、 `GetMetaDataInterface` モジュールの [IMetaDataEmit](../metadata/imetadataemit-interface.md) interface オブジェクトを取得し、 [IMetaDataEmit:: savetomemory](../metadata/imetadataemit-savetomemory-method.md) を呼び出してモジュールのメタデータのコピーをメモリに保存します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Metadata](../metadata/index.md)
