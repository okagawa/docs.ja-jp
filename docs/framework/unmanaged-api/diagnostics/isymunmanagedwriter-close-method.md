---
title: ISymUnmanagedWriter::Close メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
ms.openlocfilehash: 1d684c14f14fcc93040798ae4ee3b8bb1df5354d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733257"
---
# <a name="isymunmanagedwriterclose-method"></a>ISymUnmanagedWriter::Close メソッド

シンボルをシンボルストアにコミットした後、シンボルライターを閉じます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="remarks"></a>注釈  

 この呼び出しの後、シンボルライターは、さらに更新するために無効になります。 シンボルをコミットせずにシンボルライターを閉じるには、代わりに [ISymUnmanagedWriter:: Abort](isymunmanagedwriter-abort-method.md) メソッドを使用します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](isymunmanagedwriter-interface.md)
