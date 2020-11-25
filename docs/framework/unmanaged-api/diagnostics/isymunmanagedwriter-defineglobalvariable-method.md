---
title: ISymUnmanagedWriter::DefineGlobalVariable メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
ms.openlocfilehash: bc389b7247a6b1d6ce16cb3cf350f1672213b2e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716422"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a>ISymUnmanagedWriter::DefineGlobalVariable メソッド

グローバル変数を 1 つ定義します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a>パラメーター  

 `name`  
 から `WCHAR` グローバル変数名を定義するへのポインター。  
  
 `attributes`  
 からグローバル変数属性。  
  
 `cSig`  
 から `ULONG32` バッファーのサイズ (文字数) を示す `signature` 。  
  
 `signature`  
 からグローバル変数シグネチャ。  
  
 `addrKind`  
 からアドレスの種類。  
  
 `addr1`  
 からパラメーター指定の最初のアドレス。  
  
 `addr2`  
 からパラメーター指定の2番目のアドレス。  
  
 `addr3`  
 からパラメーター指定の3番目のアドレス。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](isymunmanagedwriter-interface.md)
- [DefineLocalVariable メソッド](isymunmanagedwriter-definelocalvariable-method.md)
- [DefineGlobalVariable2 メソッド](isymunmanagedwriter2-defineglobalvariable2-method.md)
