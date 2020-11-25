---
title: ISymUnmanagedVariable::GetName メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type:
- apiref
ms.openlocfilehash: f9da3ca8684da3bbc87146b3b52effdc4f91393d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726887"
---
# <a name="isymunmanagedvariablegetname-method"></a>ISymUnmanagedVariable::GetName メソッド

この変数の名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a>パラメーター  

 `cchName`  
 からパラメーターが指すバッファーの長さ `pcchName` 。  
  
 `pcchName`  
 入出力 `ULONG32` Null 終了を含む、名前を格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。  
  
 `szName`  
 入出力名前を格納するバッファー。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedVariable インターフェイス](isymunmanagedvariable-interface.md)
