---
description: 詳細については、「CorValidatorModuleType 列挙型」を参照してください。
title: CorValidatorModuleType 列挙型
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
ms.openlocfilehash: 13792c461660ddd8cfd530f5b34d642d806cdea4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707242"
---
# <a name="corvalidatormoduletype-enumeration"></a>CorValidatorModuleType 列挙型

モジュールの種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|モジュールの型が無効です。|  
|`ValidatorModuleTypeMin`|列挙型の最小値 `CorValidatorModuleType` 。|  
|`ValidatorModuleTypePE`|モジュールは、移植可能な実行可能 (PE) ファイルです。|  
|`ValidatorModuleTypeObj`|モジュールは .obj ファイルです。|  
|`ValidatorModuleTypeEnc`|モジュールは、エディットコンティニュのデバッガーセッションです。|  
|`ValidatorModuleTypeIncr`|モジュールは、インクリメンタルビルドされたモジュールです。|  
|`ValidatorModuleTypeMax`|列挙型の最大値 `CorValidatorModuleType` 。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](metadata-enumerations.md)
