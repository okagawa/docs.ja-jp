---
title: ISymUnmanagedMethod::GetOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
ms.openlocfilehash: 14d4211b208482a399aa00430791b3efffda851e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699548"
---
# <a name="isymunmanagedmethodgetoffset-method"></a>ISymUnmanagedMethod::GetOffset メソッド

ドキュメント内の指定された位置に対応する、このメソッド内のオフセットを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a>パラメーター  

 `document`  
 からオフセットが要求されるドキュメントへのポインター。  
  
 `line`  
 からオフセットの要求対象となるドキュメント行。  
  
 `column`  
 からオフセットが要求されるドキュメント列。  
  
 `pRetVal`  
 入出力オフセットを受け取るへのポインター `ULONG32` 。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedMethod インターフェイス](isymunmanagedmethod-interface.md)
