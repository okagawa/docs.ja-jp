---
description: '詳細について: ISymUnmanagedWriter:: SetScopeRange メソッド'
title: ISymUnmanagedWriter::SetScopeRange メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
ms.openlocfilehash: 43cfbeaa0d366b9f2d25068cfa7b91a0fea8ac59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762059"
---
# <a name="isymunmanagedwritersetscoperange-method"></a>ISymUnmanagedWriter::SetScopeRange メソッド

指定した構文のスコープのオフセット範囲を定義します。 スコープは新しい現在のスコープになり、スコープのスタックにプッシュされます。 スコープは階層を形成する必要があります。 兄弟を重ねることはできません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a>パラメーター  

 `scopeId`  
 からスコープのスコープ識別子。  
  
 `startOffset`  
 からメソッドの先頭からの構文のスコープの最初の命令のオフセット (バイト単位)。  
  
 `endOffset`  
 からメソッドの先頭からの構文のスコープの最後の命令のオフセット (バイト単位)。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="remarks"></a>解説  

 [ISymUnmanagedWriter:: OpenScope](isymunmanagedwriter-openscope-method.md) は、 `ISymUnmanagedWriter::SetScopeRange` 後でスコープの開始オフセットと終了オフセットを定義するためにと共に使用できる非透過スコープ識別子を返します。 この場合、 `ISymUnmanagedWriter::OpenScope` と [ISymUnmanagedWriter:: cloに](isymunmanagedwriter-closescope-method.md) 渡されるオフセットは無視されます。 スコープ識別子は、現在のメソッドでのみ有効です。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](isymunmanagedwriter-interface.md)
