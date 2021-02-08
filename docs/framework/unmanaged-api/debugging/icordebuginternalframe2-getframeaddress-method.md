---
description: '詳細について: ICorDebugInternalFrame2:: Getフレームアドレスメソッド'
title: ICorDebugInternalFrame2::GetFrameAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.GetFrameAddress Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type:
- apiref
ms.openlocfilehash: bb745424680c5b9a5277badfbe2d96db46e2e3d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791115"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a>ICorDebugInternalFrame2::GetFrameAddress メソッド

内部フレームのスタックアドレスを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pAddress`  
 入出力 `CORDB_ADDRESS` 内部フレームのへのポインター。  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|内部フレームのアドレスが正常に返されました。|  
|E_FAIL|内部フレームのアドレスを返すことができませんでした。|  
|E_INVALIDARG|`pAddress` は `null` です。|  
  
## <a name="remarks"></a>解説  

 で返される値を使用して、 `pAddress` スタック上の他のフレームに対する内部フレームの位置を判断できます。 IA-64 ベースのコンピューターでも、内部フレームはスタックのみに存在し、バッキングストアへの対応するポインターは存在しません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugInternalFrame2 インターフェイス](icordebuginternalframe2-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
