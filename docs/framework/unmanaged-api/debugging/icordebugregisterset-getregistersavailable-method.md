---
description: '詳細については、次のページを参照してください: いいね!:: GetRegistersAvailable メソッド'
title: ICorDebugRegisterSet::GetRegistersAvailable メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
ms.openlocfilehash: a1727c594733fe6529fe1e78f341723623b68be2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690822"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a>ICorDebugRegisterSet::GetRegistersAvailable メソッド

[このは、この](icordebugregisterset-interface.md)"この" のどのレジスタが現在使用可能であるかを示すビットマスクを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pAvailable`  
 入出力現在使用できるレジスタを示すビットマスク。  
  
## <a name="remarks"></a>解説  

 特定の状況でその値を特定できない場合は、レジスタを使用できない可能性があります。  
  
 返されるマスクには、レジスタごとにビットが含まれています (1 << レジスタインデックス)。 レジスタが使用可能な場合、ビット値は1です。使用できない場合は0です。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRegisterSet インターフェイス](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 インターフェイス](icordebugregisterset2-interface.md)
