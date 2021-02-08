---
description: '詳細については、次を参照してください: CorDebugNGenPolicy 列挙型'
title: CorDebugNGenPolicy 列挙型
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
ms.openlocfilehash: 529a5979bacef32ce78262c122004a66b54156ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801580"
---
# <a name="cordebugngenpolicy-enumeration"></a>CorDebugNGenPolicy 列挙型

デバッガーがネイティブ イメージ キャッシュからネイティブ (NGen) イメージを読み込むかどうかを指定する値を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー名|説明|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|Windows 8.x ストアアプリでは、ローカルのネイティブイメージキャッシュからのイメージの使用は無効になっています。 デスクトップアプリでは、この設定による影響はありません。|  
  
## <a name="remarks"></a>解説  

 `CorDebugNGENPolicy`列挙体は、 [ICorDebugProcess5:: EnableNGENPolicy](icordebugprocess5-enablengenpolicy-method.md)メソッドによって使用されます。 ローカルのネイティブイメージキャッシュからのイメージの使用を無効にすると、最適化されたネイティブイメージの代わりにデバッグ可能な JIT コンパイルイメージをデバッガーが読み込むことができるため、一貫したデバッグエクスペリエンスを実現できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のデバッグ](debugging-enumerations.md)
