---
title: CorGenericParamAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorGenericParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGenericParamAttr
helpviewer_keywords:
- CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type:
- apiref
ms.openlocfilehash: ea50430c3ae6cef9b47880bcb8ad969f62ce9c39
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704917"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr 列挙型

<xref:System.Type> [IMetaDataEmit2::D efineGenericParam](imetadataemit2-definegenericparam-method.md)の呼び出しで使用される、ジェネリック型のパラメーターを記述する値を格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`gpVarianceMask`|パラメーターの分散は、インターフェイスとデリゲートのジェネリックパラメーターにのみ適用されます。|  
|`gpNonVariant`|分散が存在しないことを示します。|  
|`gpCovariant`|共変性を示します。|  
|`gpContravariant`|反変性を示します。|  
|`gpSpecialConstraintMask`|特殊な制約は、任意のパラメーターに適用でき <xref:System.Type> ます。|  
|`gpNoSpecialConstraint`|パラメーターに制約が適用されないことを示し <xref:System.Type> ます。|  
|`gpReferenceTypeConstraint`|パラメーターが参照型である必要があることを示し <xref:System.Type> ます。|  
|`gpNotNullableValueTypeConstraint`|<xref:System.Type>パラメーターが null 値にできない値型である必要があることを示します。|  
|`gpDefaultConstructorConstraint`|パラメーターを受け取らない既定のパブリックコンストラクターがパラメーターに必要であることを示し <xref:System.Type> ます。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorHdr. h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](metadata-enumerations.md)
