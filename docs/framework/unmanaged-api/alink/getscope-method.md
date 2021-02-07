---
description: '詳細情報: GetScope メソッド'
title: GetScope メソッド
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
ms.openlocfilehash: cdebda457573e70755b49798ae86eae8f076216b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718360"
---
# <a name="getscope-method"></a>GetScope メソッド

インポートスコープを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `AssemblyID`  
 インポート先のアセンブリの一意の ID。  
  
 `FileToken`  
 インポート元のファイルの一意の ID。  
  
 `dwScope`  
 インポートする0から始まるスコープ。  
  
 `ppImportScope`  
 スコープの [IMetaDataImport インターフェイス](../metadata/imetadataimport-interface.md) インターフェイスを受け取ります。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK を返します。  
  
## <a name="requirements"></a>要件  

 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
