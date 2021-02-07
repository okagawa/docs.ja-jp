---
description: '詳細については、次を参照してください: EnumerateAppDomains Method:: メソッド'
title: ICorDebugProcess::EnumerateAppDomains メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnumerateAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnumerateAppDomains
helpviewer_keywords:
- ICorDebugProcess::EnumerateAppDomains method [.NET Framework debugging]
- EnumerateAppDomains method [.NET Framework debugging]
ms.assetid: d508981f-e2b2-445b-a649-69951c22702d
topic_type:
- apiref
ms.openlocfilehash: d212fafe7ae1355ba69e07b88c3b96119371fe43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691524"
---
# <a name="icordebugprocessenumerateappdomains-method"></a>ICorDebugProcess::EnumerateAppDomains メソッド

このプロセス内のすべてのアプリケーションドメインを列挙します。  
  
## <a name="syntax"></a>構文  
  
``` cpp
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppAppDomains`  
 入出力このプロセス内のアプリケーションドメインの列挙子である [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) のアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 このメソッド [は、によって](icordebugmanagedcallback-createprocess-method.md) 使用できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
