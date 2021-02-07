---
description: '詳細について: ICoreClrDebugTarget:: FreeMemory メソッド'
title: ICoreClrDebugTarget::FreeMemory メソッド
ms.date: 03/30/2017
api_name:
- ICoreDebugTarget.FreeMemory
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::FreeMemory
helpviewer_keywords:
- remote debugging API [Silverlight]
- FreeMemory method, ICoreClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::FreeMemory method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 98f2a0db-a6ec-4f9b-861d-f82485237d08
topic_type:
- apiref
ms.openlocfilehash: 9572e0c3df1fdd064e78ba170d39c1415c68dc85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690003"
---
# <a name="icoreclrdebugtargetfreememory-method"></a>ICoreClrDebugTarget::FreeMemory メソッド

[ICoreClrDebugTarget:: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md)メソッドおよび[ICoreClrDebugTarget:: enumruntimes](icoreclrdebugtarget-enumruntimes-method.md)メソッドによって割り当てられたメモリを解放します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pMemory`  
 から [ICoreClrDebugTarget:: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) または [ICoreClrDebugTarget:: enumruntimes](icoreclrdebugtarget-enumruntimes-method.md) メソッドによって返される配列へのポインター。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Coreclrremoteデバッグインターフェイス .h  
  
 **ライブラリ:** mscordbi_macx86.dll  
  
 **.NET Framework のバージョン:** 3.5 SP1  
  
## <a name="see-also"></a>関連項目

- [ICoreClrDebugTarget インターフェイス](icoreclrdebugtarget-interface.md)
