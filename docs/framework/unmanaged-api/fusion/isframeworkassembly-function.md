---
description: '詳細情報: IsFrameworkAssembly 関数'
title: IsFrameworkAssembly 関数
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
ms.openlocfilehash: 8f264df7b1ae5c494298b11ebd94cc93aed5543a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800020"
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly 関数

指定したアセンブリが管理されているかどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a>パラメーター  

 `pwzAssemblyReference`  
 から確認するアセンブリの名前。  
  
 `pbIsFrameworkAssembly`  
 入出力アセンブリが管理されているかどうかを示すブール値。  
  
 `pwzFrameworkAssemblyIdentity`  
 からアセンブリの一意の id を含む、正規化されていない文字列。  
  
 `pccSize`  
 [入力] `pwzFrameworkAssemblyIdentity` のサイズ。  
  
## <a name="remarks"></a>解説  

 パラメーターは、 `pwzAssemblyReference` アセンブリの名前を含む文字列へのポインターです。  
  
 このアセンブリが .NET Framework の一部である場合、 `pbIsFrameworkAssembly` パラメーターにはのブール値が格納され `true` ます。  
  
 名前付きアセンブリが .NET Framework に含まれていない場合、またはパラメーターがアセンブリの名前を指定しない場合 `pwzAssemblyReference` 、に `pbIsFrameworkAssembly` はブール値のが格納され `false` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [Fusion グローバル静的関数](fusion-global-static-functions.md)
