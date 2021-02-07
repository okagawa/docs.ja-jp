---
description: '詳細については、次の情報を参照してください: GetILCode メソッド'
title: ICorDebugFunction::GetILCode メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
ms.openlocfilehash: 3b7bb29a028b189b24d3fbf02edc8190d9989a51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692525"
---
# <a name="icordebugfunctiongetilcode-method"></a>ICorDebugFunction::GetILCode メソッド

このオブジェクトに関連付けられている MSIL (Microsoft 中間言語) コードを表す、コードインスタンスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppCode`  
 入出力インスタンスへのポインター。 `ICorDebugCode` 関数が MSIL にコンパイルされなかった場合は null。  
  
## <a name="remarks"></a>解説  

 この関数でエディットコンティニュが許可されている場合、メソッドは、 `GetILCode` 共通言語ランタイム (CLR) で、この関数の編集されたバージョンのコードに対応する MSIL コードを取得します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
