---
title: ISymUnmanagedConstant::GetSignature メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
ms.openlocfilehash: 4436e4528c1dc486eb5c443c5a9467ac69a26c7d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706932"
---
# <a name="isymunmanagedconstantgetsignature-method"></a>ISymUnmanagedConstant::GetSignature メソッド

定数の署名を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a>パラメーター  

 `cSig`  
 からパラメーターが指すバッファーの長さ `pcSig` 。  
  
 `pcSig`  
 入出力 `ULONG32` 署名を格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。  
  
 `sig`  
 入出力署名を格納するバッファー。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedConstant インターフェイス](isymunmanagedconstant-interface.md)
- [GetName メソッド](isymunmanagedconstant-getname-method.md)
- [GetValue メソッド](isymunmanagedconstant-getvalue-method.md)
