---
description: '詳細について: ICLRDataTarget:: GetMachineType メソッド'
title: ICLRDataTarget::GetMachineType メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetMachineType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetMachineType
helpviewer_keywords:
- ICLRDataTarget::GetMachineType method [.NET Framework debugging]
- GetMachineType method [.NET Framework debugging]
ms.assetid: 5f1f9c61-3e3b-48b2-b111-a4395f7623a7
topic_type:
- apiref
ms.openlocfilehash: 5624f734a77f51b4ea6cd9dd0c9df393c72e7d26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801346"
---
# <a name="iclrdatatargetgetmachinetype-method"></a>ICLRDataTarget::GetMachineType メソッド

ターゲットプロセスが使用している命令セットの種類の識別子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `machineType`  
 入出力ターゲットプロセスが使用している命令セットを示す値へのポインター。 返されるは、 `machineType` winnt.h ヘッダーファイルで定義されている IMAGE_FILE_MACHINE 定数の1つです。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** ClrData .idl, ClrData .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRDataTarget インターフェイス](iclrdatatarget-interface.md)
