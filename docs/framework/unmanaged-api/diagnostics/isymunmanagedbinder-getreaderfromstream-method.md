---
title: ISymUnmanagedBinder::GetReaderFromStream メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
ms.openlocfilehash: 2d927b02b7deebecb53a2218e2ec0275a07307b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706958"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a>ISymUnmanagedBinder::GetReaderFromStream メソッド

メタデータインターフェイスと、シンボルストアを含むストリームが指定された場合、は、指定されたシンボルストアからデバッグシンボルを読み取る正しい [ISymUnmanagedReader](isymunmanagedreader-interface.md) 構造体を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a>パラメーター  

 `importer`  
 からメタデータインポートインターフェイスへのポインター。  
  
 `pstream`  
 からシンボルストアが格納されているストリームへのポインター。  
  
 `pRetVal`  
 入出力返された [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスに設定されたポインター。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedBinder インターフェイス](isymunmanagedbinder-interface.md)
