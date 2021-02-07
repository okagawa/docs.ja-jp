---
description: '詳細については、次を参照してください: StackOverflowInfo 構造体'
title: StackOverflowInfo 構造体
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
ms.openlocfilehash: cca65e4293c05b89ebefc3c6dd36a6b8898eb15f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679395"
---
# <a name="stackoverflowinfo-structure"></a>StackOverflowInfo 構造体

発生したオーバーフローの種類とオーバーフローによってスローされた例外に関する情報を格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`soType`|オーバーフローの種類を指定する [StackOverflowType](stackoverflowtype-enumeration.md) 列挙体の値。|  
|`pExceptionInfo`|Win32 オブジェクトへのポインター。このオブジェクトには、例外 `EXCEPTION_POINTERS` のコンピューターに依存しない記述と、例外の発生時にプロセッサコンテキストのコンピューターに依存する記述を持つコンテキストレコードが含まれています。|  
  
## <a name="remarks"></a>解説  

 `StackOverflowInfo`オブジェクトは、イベントの[Iactiononclrevent:: OnEvent](iactiononclrevent-onevent-method.md)メソッドに渡され `Event_StackOverflow` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト構造体](hosting-structures.md)
