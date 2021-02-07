---
description: '詳細について: ICorDebugClass2:: SetJMCStatus メソッド'
title: ICorDebugClass2::SetJMCStatus メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
ms.openlocfilehash: 28859522052fd9587dc3890eb4137929dbdc6763
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711477"
---
# <a name="icordebugclass2setjmcstatus-method"></a>ICorDebugClass2::SetJMCStatus メソッド

クラスの各メソッドについて、メソッドがユーザー定義のコードかどうかを示す値を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `bIsJustMyCode`  
 から `true` メソッドがユーザー定義コードであることを示す場合はに設定します。それ以外の場合はに設定 `false` します。  
  
## <a name="remarks"></a>解説  

 マイコードのみ (JMC) のステッパは、ユーザー定義ではないコードをスキップします。 ユーザー定義コードは、デバッグ可能なコードのサブセットである必要があります。  
  
 `SetJMCStatus` は、他のすべてのメソッドの値が正常に設定された場合でも、メソッドの値の設定に失敗した場合に S_FALSE の HRESULT 値を返します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
