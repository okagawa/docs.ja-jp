---
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
ms.openlocfilehash: e8c6fd7dca13afe7504e447caca9a217c8136c27
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684526"
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
