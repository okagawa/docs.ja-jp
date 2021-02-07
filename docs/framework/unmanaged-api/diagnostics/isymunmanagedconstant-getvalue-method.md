---
description: '詳細情報: ISymUnmanagedConstant:: GetValue メソッド'
title: ISymUnmanagedConstant::GetValue メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetValue
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetValue
helpviewer_keywords:
- GetValue method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetValue method [.NET Framework debugging]
ms.assetid: 0036fc10-e768-47a8-b9cf-bf47faf8d194
topic_type:
- apiref
ms.openlocfilehash: 05818028deb804bf2a2426285b5185b01776199d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689691"
---
# <a name="isymunmanagedconstantgetvalue-method"></a>ISymUnmanagedConstant::GetValue メソッド

定数の値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pValue`  
 入出力値を受け取る変数へのポインター。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedConstant インターフェイス](isymunmanagedconstant-interface.md)
- [GetName メソッド](isymunmanagedconstant-getname-method.md)
- [GetSignature メソッド](isymunmanagedconstant-getsignature-method.md)
