---
description: '詳細情報: ISymUnmanagedWriter:: Close メソッド'
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
ms.openlocfilehash: 02f4d8d4a232240160ad5065947282f40af42f4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762631"
---
# <a name="isymunmanagedwriterclose-method"></a>ISymUnmanagedWriter::Close メソッド

シンボルをシンボルストアにコミットした後、シンボルライターを閉じます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="remarks"></a>解説  

 この呼び出しの後、シンボルライターは、さらに更新するために無効になります。 シンボルをコミットせずにシンボルライターを閉じるには、代わりに [ISymUnmanagedWriter:: Abort](isymunmanagedwriter-abort-method.md) メソッドを使用します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](isymunmanagedwriter-interface.md)
