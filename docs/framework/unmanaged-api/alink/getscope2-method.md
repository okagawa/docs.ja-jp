---
description: '詳細情報: GetScope2 メソッド'
title: GetScope2 メソッド
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
ms.openlocfilehash: 9a68f02a638b58e7a70207d8610607bf24b2b96b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718344"
---
# <a name="getscope2-method"></a>GetScope2 メソッド

インポートスコープを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;
```  
  
## <a name="parameters"></a>パラメーター  

 `AssemblyID`  
 ターゲットアセンブリの ID。  
  
 `FileToken`  
 インポート元のファイルの ID。  
  
 `dwScope`  
 インポートする0から始まるスコープ。  
  
 `ppImportScope`  
 指定されたスコープの [IMetaDataImport2 インターフェイス](../metadata/imetadataimport2-interface.md) インターフェイスへのポインターを受け取ります。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK を返します。  
  
## <a name="requirements"></a>要件  

 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink2 インターフェイス](ialink2-interface.md)
- [IALink インターフェイス](ialink-interface.md)
- [ALink API](index.md)
