---
description: 詳細については、次のページを参照してください
title: 'いい変数 Home:: GetRegister メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
ms.openlocfilehash: c394d455048cf7451b8320ed72a6aa7adfb3518e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790660"
---
# <a name="icordebugvariablehomegetregister-method"></a>いい変数 Home:: GetRegister メソッド

の場所の種類がである変数 `VLT_REGISTER` と、の場所の種類がの変数の基本レジスタを含むレジスタを取得し `VLT_REGISTER_RELATIVE` ます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pRegister`  
 入出力の場所の種類がである変数のレジスタ、 `VLT_REGISTER` およびの場所の種類がの変数の基本レジスタを示す CorDebugRegister 列挙値 `VLT_REGISTER_RELATIVE` 。  
  
## <a name="return-value"></a>戻り値  

 メソッドは、次の値を返します。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|変数は、引数で指定されたレジスタにあり `pRegister` ます。|  
|`E_FAIL`|変数がレジスタまたはレジスタの相対位置にありません。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [VariableLocationType 列挙型](variablelocationtype-enumeration.md)
- [ICorDebugVariableHome インターフェイス](icordebugvariablehome-interface.md)
