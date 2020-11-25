---
title: CorFileMapping 列挙体
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
ms.openlocfilehash: 63e27a62e176a92b03c10b59a55d9da3192918f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726117"
---
# <a name="corfilemapping-enumeration"></a>CorFileMapping 列挙体

[IMetaDataInfo:: GetFileMapping](imetadatainfo-getfilemapping-method.md)メソッドの呼び出しから返されるファイルマッピングの種類を記述する値を格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`fmFlat`|ファイルはデータファイルとしてマップされます。 つまり、フラグは `SEC_IMAGE` Microsoft Win32 関数に渡されませんでした `CreateFileMapping` 。|  
|`fmExecutableImage`|`LoadLibrary`関数または関数をフラグと共に使用することで、ファイルは実行用にマップされ `CreateFileMapping` `SEC_IMAGE` ます。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorHdr. h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](metadata-enumerations.md)
- [GetFileMapping メソッド](imetadatainfo-getfilemapping-method.md)
