---
description: '詳細については、次のページを参照してください: いいね:: の GetObject メソッド'
title: ICorDebugAppDomain::GetObject メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetObject
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type:
- apiref
ms.openlocfilehash: 59389e2a4ca72f8dcdd7117213e968440d30aaa6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754213"
---
# <a name="icordebugappdomaingetobject-method"></a>ICorDebugAppDomain::GetObject メソッド

共通言語ランタイム (CLR) アプリケーションドメインへのインターフェイスポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppObject`  
 入出力CLR アプリケーションドメインを表す ICorDebugValue インターフェイスオブジェクトのアドレスへのポインター。  
  
## <a name="return-value"></a>戻り値  

 <xref:System.AppDomain?displayProperty=nameWithType>このアプリケーションドメインに対してマネージオブジェクトが構築されていない場合、メソッドはを返し、を `S_FALSE` に配置し `NULL` `*ppObject` ます。  
  
## <a name="remarks"></a>解説  

 プロセス内の各アプリケーションドメインは、 <xref:System.AppDomain?displayProperty=nameWithType> それを表すランタイムにマネージオブジェクトを持つことができます。 この関数は、このマネージオブジェクトに対応する ICorDebugValue インターフェイスオブジェクトを取得し <xref:System.AppDomain?displayProperty=nameWithType> ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
