---
description: '詳細については、次を参照してください: いいね:: 終了メソッド'
title: ICorDebugController::Terminate メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
ms.openlocfilehash: 15cc832205ebfe86e521d4a45124808e0f3fe128
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710713"
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate メソッド

指定された終了コードを使用してプロセスを終了します。  
  
> [!NOTE]
> このメソッドは、Win32 関数のラッパーです `TerminateProcess` 。 したがって、は、 `Terminate` Win32 関数が使用するのと同じ方法で終了コードを使用し `TerminateProcess` ます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `exitCode`  
 から終了コードを表す数値。 有効な数値は、Winbase. h で定義されています。  
  
## <a name="remarks"></a>解説  

 が呼び出されたときにプロセスが停止された場合は、このプロセスを続行 `Terminate` する必要があります。これを行うに[は、](icordebugcontroller-continue-method.md)デバッガーが、"ExitProcess" または " [](icordebugmanagedcallback-exitprocess-method.md) [managedcallback:: exitappdomain](icordebugmanagedcallback-exitappdomain-method.md) callback" を使用して終了の確認を受け取るようにします。  
  
> [!NOTE]
> このメソッドは、アプリケーションドメインによって実装されていません。 つまり、レベルでは実装されていません <xref:System.AppDomain> 。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
