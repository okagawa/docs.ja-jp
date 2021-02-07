---
description: '詳細について: ISymUnmanagedReader:: GetGlobalVariables メソッド'
title: ISymUnmanagedReader::GetGlobalVariables メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetGlobalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetGlobalVariables
helpviewer_keywords:
- GetGlobalVariables method [.NET Framework debugging]
- ISymUnmanagedReader::GetGlobalVariables method [.NET Framework debugging]
ms.assetid: a2dd5098-3e58-4be5-b7a2-e4160b3b505a
topic_type:
- apiref
ms.openlocfilehash: 2b017d2a5746942f701cf79d3d29f1eb571dceab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689652"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a>ISymUnmanagedReader::GetGlobalVariables メソッド

すべてのグローバル変数を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a>パラメーター  

 `cVars`  
 からが指すバッファーの長さ `pcVars` 。  
  
 `pcVars`  
 入出力 `ULONG32` 変数を格納するために必要なバッファーのサイズを受け取るへのポインター。  
  
 `pVars`  
 入出力変数を格納しているバッファー。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedReader インターフェイス](isymunmanagedreader-interface.md)
