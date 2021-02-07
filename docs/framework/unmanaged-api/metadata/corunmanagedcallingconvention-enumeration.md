---
description: '詳細については、次を参照してください: CorUnmanagedCallingConvention 列挙型'
title: CorUnmanagedCallingConvention 列挙型
ms.date: 03/30/2017
api_name:
- CorUnmanagedCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnmanagedCallingConvention
helpviewer_keywords:
- CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type:
- apiref
ms.openlocfilehash: a4b5c70b7dcb4750d641540662941ed3cc08c94b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707294"
---
# <a name="corunmanagedcallingconvention-enumeration"></a>CorUnmanagedCallingConvention 列挙型

アンマネージコードの呼び出し規約を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorUnmanagedCallingConvention {  
  
    IMAGE_CEE_UNMANAGED_CALLCONV_C         = 0x1,  
    IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL   = 0x2,  
    IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL  = 0x3,  
    IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL  = 0x4,  
  
    IMAGE_CEE_CS_CALLCONV_C                = 0x1,  
    IMAGE_CEE_CS_CALLCONV_STDCALL          = 0x2,  
    IMAGE_CEE_CS_CALLCONV_THISCALL         = 0x3,  
    IMAGE_CEE_CS_CALLCONV_FASTCALL         = 0x4  
  
} CorUnmanagedCallingConvention;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|C 言語の呼び出し規約。|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|標準の呼び出し規約。|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|"This" 呼び出し規約。|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|"高速" 呼び出し規約。|  
|`IMAGE_CEE_CS_CALLCONV_C`|使用しません。|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|使用しません。|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|使用しません。|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|使用しません。|  
  
## <a name="remarks"></a>解説  

 CLR では、.NET Framework バージョン1.0 での "高速" 呼び出し規約はサポートされていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorHdr. h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](metadata-enumerations.md)
