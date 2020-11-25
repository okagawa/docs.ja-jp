---
title: WAITORTIMERCALLBACK 関数ポインター
ms.date: 03/30/2017
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
ms.openlocfilehash: 74256f35804ff59f04952a1ac20ac7866e8f5683
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732815"
---
# <a name="waitortimercallback-function-pointer"></a>WAITORTIMERCALLBACK 関数ポインター

待機ハンドル () がシグナル状態になったか、タイムアウトしたことをホストに通知する関数を指し <xref:System.Threading.WaitHandle> ます。  
  
 この関数ポインターは .NET Framework 4 で非推奨とされました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `lpParameter`  
 からホストによって定義された情報を格納しているオブジェクトへのポインター。  
  
 `TimerOrWaitFired`  
 [入力] `true` 待機ハンドルがタイムアウトした場合は `false` 。それがシグナル状態だった場合は。  
  
## <a name="remarks"></a>注釈  

 `WAITORTIMERCALLBACK`ポイントがコールバック関数であり、ホストアプリケーションのライターによって実装されている必要がある関数。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorWks.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](deprecated-clr-hosting-functions.md)
