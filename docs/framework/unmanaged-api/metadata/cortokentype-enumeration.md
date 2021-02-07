---
description: 詳細については、「CorTokenType 列挙型」を参照してください。
title: CorTokenType 列挙型
ms.date: 03/30/2017
api_name:
- CorTokenType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTokenType
helpviewer_keywords:
- CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type:
- apiref
ms.openlocfilehash: 954bddccd8fe20be46080f8843bcf754e0cf1bbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678407"
---
# <a name="cortokentype-enumeration"></a>CorTokenType 列挙型

メタデータトークンの種類を示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`mdtModule`|`mdModule`トークン。|  
|`mdtTypeRef`|`mdTypeRef`トークン。|  
|`mdtTypeDef`|`mdTypeDef`トークン。|  
|`mdtFieldDef`|`mdFieldDef`トークン。|  
|`mdtMethodDef`|`mdMethodDef`トークン。|  
|`mdtParamDef`|`mdParamDef`トークン。|  
|`mdtInterfaceImpl`|`mdInterfaceImpl`トークン。|  
|`mdtMemberRef`|`mdMemberRef`トークン。|  
|`mdtCustomAttribute`|`mdCustomAttribute`トークン。|  
|`mdtPermission`|`mdPermission`トークン。|  
|`mdtSignature`|`mdSignature`トークン。|  
|`mdtEvent`|`mdEvent`トークン。|  
|`mdtProperty`|`mdProperty`トークン。|  
|`mdtModuleRef`|`mdModuleRef`トークン。|  
|`mdtTypeSpec`|`mdTypeSpec`トークン。|  
|`mdtAssembly`|`mdAssembly`トークン。|  
|`mdtAssemblyRef`|`mdAssemblyRef`トークン。|  
|`mdtFile`|`mdFile`トークン。|  
|`mdtExportedType`|`mdExportedType`トークン。|  
|`mdtManifestResource`|`mdManifestResource`トークン。|  
|`mdtGenericParam`|`mdGenericParam`トークン。|  
|`mdtMethodSpec`|`mdMethodSpec`トークン。|  
|`mdtGenericParamConstraint`|`mdGenericParamConstraint`トークン。|  
|`mdtString`|`mdString`トークン。|  
|`mdtName`|`mdName`トークン。|  
|`mdtBaseType`|使用されていません。|  
  
## <a name="remarks"></a>解説  

 各値は、対応するメタデータトークンの上位バイトの値に相当します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorHdr. h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](metadata-enumerations.md)
