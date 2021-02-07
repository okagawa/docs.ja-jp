---
description: '詳細については、次のページを参照してください:: テキストの表示方法'
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
ms.openlocfilehash: f3977d4fbe57b24e7b98b7a597b0db7ad171eb1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691875"
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
  
## <a name="remarks"></a>解説  

 命令ポインターの値は、関数の MSIL (Microsoft 中間言語) コードへのスタックフレームのオフセットです。 スタックフレームがアクティブな場合、このアドレスは次に実行する命令になります。 スタックフレームがアクティブでない場合、このアドレスはスタックフレームが再アクティブ化されたときに次に実行される命令になります。  
  
 このフレームが just-in-time (JIT) でコンパイルされたフレームである場合、命令ポインターの値は、実際のネイティブ命令ポインターから逆方向にマッピングすることによって決定されます。したがって、値は概数にすぎない可能性があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
