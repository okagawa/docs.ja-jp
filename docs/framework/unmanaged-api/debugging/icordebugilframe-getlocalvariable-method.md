---
description: '詳細については、次のページを参照してください:: テキストの追加方法'
title: ICorDebugILFrame::GetLocalVariable メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetLocalVariable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type:
- apiref
ms.openlocfilehash: c4bb3e5a5d970539607efbaf55f3f7f08f7e72af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791375"
---
# <a name="icordebugilframegetlocalvariable-method"></a>ICorDebugILFrame::GetLocalVariable メソッド

この MSIL (Microsoft 中間言語) スタックフレーム内の指定されたローカル変数の値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `dwIndex`  
 からこの MSIL スタックフレーム内のローカル変数のインデックス。  
  
 `ppValue`  
 [out] 取得した値を表す ICorDebugValue オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 メソッドは、 `GetLocalVariable` MSIL スタックフレーム内または just-in-time (JIT) コンパイルフレームで使用できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
