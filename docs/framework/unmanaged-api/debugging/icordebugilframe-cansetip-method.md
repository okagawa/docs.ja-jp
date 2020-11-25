---
title: ICorDebugILFrame::CanSetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
ms.openlocfilehash: 99c80fba594e9eaf69a3cc9a025509aa4c3c26a4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703305"
---
# <a name="icordebugilframecansetip-method"></a>ICorDebugILFrame::CanSetIP メソッド

命令ポインターを Microsoft 中間言語 (MSIL) コード内の指定したオフセット位置に安全に設定できるかどうかを示す HRESULT を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `nOffset`  
 から命令ポインターに必要な設定。  
  
## <a name="remarks"></a>注釈  

 次のように、メソッドを使用します。 `CanSetIP` [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) が `CanSetIP` S_OK 以外の HRESULT を返した場合でもを呼び出すことはでき `ICorDebugILFrame::SetIP` ますが、デバッガーがデバッグ中のコードの安全かつ適切な実行を継続する保証はありません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug、h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
