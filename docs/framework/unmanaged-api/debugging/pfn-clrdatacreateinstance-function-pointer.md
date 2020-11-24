---
title: PFN_CLRDataCreateInstance 関数ポインター
ms.date: 03/30/2017
api_name:
- PFN_CLRDataCreateInstance
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- PFN_CLRDataCreateInstance
helpviewer_keywords:
- PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type:
- apiref
ms.openlocfilehash: 68a5b8bb1568f10699653479357b02b2e847cc02
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671968"
---
# <a name="pfn_clrdatacreateinstance-function-pointer"></a>PFN_CLRDataCreateInstance 関数ポインター

指定されたターゲット項目のインターフェイスオブジェクトを作成する関数を指します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `iid`  
 からインスタンス化するインターフェイスの識別子。  
  
 `target`  
 からインターフェイスオブジェクトの作成対象となる項目を表す、ユーザーによって実装された [ICLRDataTarget](iclrdatatarget-interface.md) オブジェクトへのポインター。  
  
 `iface`  
 入出力返されたインターフェイスオブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>注釈  

 `ICLRDataTarget`オブジェクトは、デバッグアプリケーションのライターによって実装されます。 実装は、表示されるターゲット項目の種類によって異なります。 ターゲット項目には、プロセス、メモリダンプ、リモートコンピューターなどがあります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** ClrData .idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ グローバル静的関数](debugging-global-static-functions.md)
