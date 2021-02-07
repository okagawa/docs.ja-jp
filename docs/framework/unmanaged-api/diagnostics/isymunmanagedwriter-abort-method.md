---
description: '詳細について: ISymUnmanagedWriter:: Abort メソッド'
title: ISymUnmanagedWriter::Abort メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
ms.openlocfilehash: 312694bf2b667ea78bf5ddc993d0e2b71c85a8ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762683"
---
# <a name="isymunmanagedwriterabort-method"></a>ISymUnmanagedWriter::Abort メソッド

シンボルストアにシンボルをコミットせずにシンボルライターを閉じます。 この呼び出しの後、シンボルライターは、さらに更新するために無効になります。 シンボルをコミットし、シンボルライターを閉じるには、代わりに [ISymUnmanagedWriter:: close](isymunmanagedwriter-close-method.md) メソッドを使用します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](isymunmanagedwriter-interface.md)
