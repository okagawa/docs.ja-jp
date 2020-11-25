---
title: EInitializeNewDomainFlags 列挙体
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
ms.openlocfilehash: 8350b507609e63c060cda08514200d386c37a6b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724326"
---
# <a name="einitializenewdomainflags-enumeration"></a>EInitializeNewDomainFlags 列挙体

ホストがアプリケーションドメインの初期化に関する情報をランタイムに提供できるようにします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|フラグなし。|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|ホストがメソッド内のアプリケーションドメインのセキュリティ状態に変更を加えないことを、共通言語ランタイム (CLR) に通知し <xref:System.AppDomainManager.InitializeNewDomain%2A> ます。|  
  
## <a name="remarks"></a>注釈  

 [ICLRDomainManager:: SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md)メソッドは、型のパラメーターを受け取り `EInitializeNewDomainFlags` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスティングの列挙型](hosting-enumerations.md)
- [SetAppDomainManagerType メソッド](iclrdomainmanager-setappdomainmanagertype-method.md)
