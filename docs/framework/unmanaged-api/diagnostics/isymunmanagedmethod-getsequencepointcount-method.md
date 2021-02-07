---
description: '詳細について: ISymUnmanagedMethod:: GetSequencePointCount メソッド'
title: ISymUnmanagedMethod::GetSequencePointCount メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePointCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePointCount
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePointCount method [.NET Framework debugging]
- GetSequencePointCount method [.NET Framework debugging]
ms.assetid: 836133e8-6108-4b9b-b0a9-bce4e08dccda
topic_type:
- apiref
ms.openlocfilehash: 6e0341ddc151454de8764a47a92556ab1925bfa1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710005"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a>ISymUnmanagedMethod::GetSequencePointCount メソッド

このメソッド内のシーケンスポイントの数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pRetVal`  
 入出力 `ULONG32` シーケンスポイントを格納するために必要なバッファーのサイズを受け取るへのポインター。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedMethod インターフェイス](isymunmanagedmethod-interface.md)
