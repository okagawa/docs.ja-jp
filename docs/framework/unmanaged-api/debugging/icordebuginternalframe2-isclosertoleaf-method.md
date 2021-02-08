---
description: '詳細について: ICorDebugInternalFrame2:: IsCloserToLeaf メソッド'
title: ICorDebugInternalFrame2::IsCloserToLeaf メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type:
- apiref
ms.openlocfilehash: d773f8670f600a5bcd2a8dad7f23fe243195957c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801281"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a>ICorDebugInternalFrame2::IsCloserToLeaf メソッド

内部フレームが、指定されたのは、指定されたとしての `this` オブジェクトよりもリーフの近くにあるかどうかを確認します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pFrameToCompare`  
 から比較オブジェクトへのポインター `ICorDebugFrame` 。  
  
 `pIsCloser`  
 [出力] `true``this`内部フレームがで指定されたフレームよりもリーフの近くにある場合は `pFrameToCompare` 。それ以外の場合は `false` 。  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|比較が正常に実行されました。|  
|E_FAIL|比較を実行できませんでした。|  
|E_INVALIDARG|`pFrameToCompare` または `pIsCloser` が null です。|  
  
## <a name="remarks"></a>解説  

 `IsCloserToLeaf` を使用すると、スタック上の他のフレームと内部フレームをインターリーブするポリシーを実装できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugInternalFrame2 インターフェイス](icordebuginternalframe2-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
