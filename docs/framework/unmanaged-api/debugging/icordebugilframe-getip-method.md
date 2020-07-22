---
title: ICorDebugILFrame::GetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
ms.openlocfilehash: 3890cb4236f113bc6efc23bfb606d19a525ec234
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210268"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP メソッド
命令ポインターの値と、命令ポインターの値が取得された方法を示すビットごとの組み合わせ値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pnOffset`  
 入出力命令ポインターの値。  
  
 `pMappingResult`  
 入出力命令ポインターの値の取得方法を示す CorDebugMappingResult 列挙値のビットごとの組み合わせへのポインター。  
  
## <a name="remarks"></a>Remarks  
 命令ポインターの値は、関数の MSIL (Microsoft 中間言語) コードへのスタックフレームのオフセットです。 スタックフレームがアクティブな場合、このアドレスは次に実行する命令になります。 スタックフレームがアクティブでない場合、このアドレスはスタックフレームが再アクティブ化されたときに次に実行される命令になります。  
  
 このフレームが just-in-time (JIT) でコンパイルされたフレームである場合、命令ポインターの値は、実際のネイティブ命令ポインターから逆方向にマッピングすることによって決定されます。したがって、値は概数にすぎない可能性があります。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
