---
description: '詳細について: ICorDebugProcess7:: SetWriteableMetadataUpdateMode メソッド'
title: ICorDebugProcess7::SetWriteableMetadataUpdateMode メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type:
- apiref
ms.openlocfilehash: 86ece68e160fbd61f44adcf495656c7b5d6b5153
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691264"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a>ICorDebugProcess7::SetWriteableMetadataUpdateMode メソッド

[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 デバッガーが、ターゲット プロセス内のメタデータに対するメモリ内更新をどのように処理するかを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `flags`  
 ターゲットプロセス内のメタデータに対するメモリ内更新をデバッガーに対して表示 () するか、非表示 () するかを指定する [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) 列挙値です `WriteableMetadataUpdateMode::AlwaysShowUpdates` `WriteableMetadataUpdateMode::LegacyCompatPolicy` 。  
  
## <a name="remarks"></a>解説  

 ターゲット プロセスのメタデータに対する更新は、[編集]、[続行] で行うか、プロファイラー、または <xref:System.Reflection.Emit?displayProperty=nameWithType> で行うことができます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess7 インターフェイス](icordebugprocess7-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
