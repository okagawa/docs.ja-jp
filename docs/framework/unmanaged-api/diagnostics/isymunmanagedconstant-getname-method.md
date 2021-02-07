---
description: '詳細情報: ISymUnmanagedConstant:: GetName メソッド'
title: ISymUnmanagedConstant::GetName メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
ms.openlocfilehash: 57531711ed60c9e35e749a3cb1f1ba5d5c48ca66
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689821"
---
# <a name="isymunmanagedconstantgetname-method"></a>ISymUnmanagedConstant::GetName メソッド

定数の名前を取得します。  
  
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
 からパラメーターが指すバッファーの長さ `szName` 。  
  
 `pcchName`  
 入出力 `ULONG32` Null 終了を含む、名前を格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。  
  
 `szName`  
 入出力名前を格納するバッファー。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedConstant インターフェイス](isymunmanagedconstant-interface.md)
- [GetSignature メソッド](isymunmanagedconstant-getsignature-method.md)
- [GetValue メソッド](isymunmanagedconstant-getvalue-method.md)
