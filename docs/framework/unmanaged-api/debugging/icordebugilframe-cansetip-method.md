---
description: '詳細については、次の情報を参照してください:: テキストの表示方法'
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
ms.openlocfilehash: d6ba0d073e8807ac6173f7f3e3982fe1d3eb4e01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791440"
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
  
## <a name="remarks"></a>解説  

 次のように、メソッドを使用します。 `CanSetIP` [](icordebugilframe-setip-method.md) が `CanSetIP` S_OK 以外の HRESULT を返した場合でもを呼び出すことはでき `ICorDebugILFrame::SetIP` ますが、デバッガーがデバッグ中のコードの安全かつ適切な実行を継続する保証はありません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug、h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
