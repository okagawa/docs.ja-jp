---
description: '詳細情報: COINITIEE 列挙型'
title: COINITIEE 列挙型
ms.date: 03/30/2017
api_name:
- COINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITIEE
helpviewer_keywords:
- COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type:
- apiref
ms.openlocfilehash: c17980582903a29cdfe33c64200c31f29ddeb17c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678608"
---
# <a name="coinitiee-enumeration"></a>COINITIEE 列挙型

共通言語ランタイムを初期化するときに [Coinitializeee](../hosting/coinitializeee-function.md) によって使用される定数を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|既定の初期化モード。 これにより、ランタイムが初期化され、既定値が作成され <xref:System.AppDomain> ます。|  
|`COINITEE_DLL`|マネージ DLL を実行するように初期化します。|  
|`COINITEE_MAIN`|マネージ EXE を実行するように初期化します。 これにより、ランタイムが初期化されますが、既定値は作成されません <xref:System.AppDomain> 。これは、EXE のメインルーチンを入力した後に作成されます。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](metadata-enumerations.md)
