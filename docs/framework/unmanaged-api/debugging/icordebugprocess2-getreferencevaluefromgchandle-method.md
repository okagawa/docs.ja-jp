---
description: '詳細について: ICorDebugProcess2:: GetReferenceValueFromGCHandle メソッド'
title: ICorDebugProcess2::GetReferenceValueFromGCHandle メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
ms.openlocfilehash: 02047dee9116d34a365242f2a532766eb60e1c81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650223"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a>ICorDebugProcess2::GetReferenceValueFromGCHandle メソッド

ガベージコレクションハンドルを持つ指定したマネージオブジェクトへの参照ポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `handle`  
 からガベージコレクションハンドルを持つマネージオブジェクトへのポインター。 この値はオブジェクトであり、 <xref:System.IntPtr> <xref:System.Runtime.InteropServices.GCHandle> マネージオブジェクトのから取得できます。  
  
 `pOutValue`  
 入出力指定したマネージオブジェクトへの参照を表す、値オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 返された参照値とガベージコレクション参照値を混同しないようにしてください。  
  
 返される参照は、通常の参照のように動作します。 ブレークポイント後にコードの実行が続行される場合は無効になります。 ターゲットオブジェクトの有効期間は、参照値の有効期間の影響を受けません。  
  
> [!NOTE]
> メソッドでは `GetReferenceValueFromGCHandle` 、ハンドルは検証されません。 したがって、 `GetReferenceValueFromGCHandle` メソッドは、無効なハンドルが渡された場合に、デバッガーとデバッグされているコードの両方を破損する可能性があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
