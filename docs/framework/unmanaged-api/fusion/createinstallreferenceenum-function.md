---
description: '詳細情報: CreateInstallReferenceEnum 関数'
title: CreateInstallReferenceEnum 関数
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
ms.openlocfilehash: cc7551707cb46bcf0c475a0095684dbc790836e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761147"
---
# <a name="createinstallreferenceenum-function"></a>CreateInstallReferenceEnum 関数

指定したアセンブリへのアプリケーションの参照のリストを表す [Iinstallreferenceenum](iinstallreferenceenum-interface.md) インスタンスへのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppRefEnum`  
 入出力返された `IInstallReferenceEnum` ポインター。  
  
 `pName`  
 から参照を列挙する対象のアセンブリを識別する [IAssemblyName](iassemblyname-interface.md) 。  
  
 `dwFlags`  
 から列挙子の動作に影響を与えるフラグ。  
  
 `pvReserved`  
 [入力] 将来の機能拡張に備えて予約されています。 `pvReserved` null 参照である必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **Library:** Fusion.dll し、Mscorwks.dll します。 Mscorwks.dll ではなく Fusion.dll を使用して、正しいバージョンの .NET Framework を対象にするようにします。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IInstallReferenceEnum インターフェイス](iinstallreferenceenum-interface.md)
- [IAssemblyName インターフェイス](iassemblyname-interface.md)
- [Fusion グローバル静的関数](fusion-global-static-functions.md)
