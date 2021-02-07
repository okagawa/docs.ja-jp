---
description: '詳細情報: ISymUnmanagedDocumentWriter:: SetCheckSum メソッド'
title: ISymUnmanagedDocumentWriter::SetCheckSum メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type:
- apiref
ms.openlocfilehash: ac2ba9654f3610dca333cf0e06c20696cf31bd1f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710089"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a>ISymUnmanagedDocumentWriter::SetCheckSum メソッド

チェックサム情報を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a>パラメーター  

 `algorithmId`  
 からアルゴリズム識別子を表す GUID。  
  
 `checkSumSize`  
 から `ULONG32` バッファーのサイズ (バイト単位) を示す `checkSum` 。  
  
 `checkSum`  
 からチェックサム情報を格納するバッファー。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedDocumentWriter インターフェイス](isymunmanageddocumentwriter-interface.md)
