---
description: '詳細について: ISymUnmanagedNamespace:: GetNamespaces メソッド'
title: ISymUnmanagedNamespace::GetNamespaces メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type:
- apiref
ms.openlocfilehash: f17b16e2a3a7001d16c86dd6dc95241c1b0785e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709907"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a>ISymUnmanagedNamespace::GetNamespaces メソッド

この名前空間の子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a>パラメーター  

 `cNameSpaces`  
 から `ULONG32` 配列のサイズを示す `namespaces` 。  
  
 `pcNameSpaces`  
 入出力 `ULONG32` 名前空間を格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。  
  
 `namespaces`  
 入出力名前空間を格納しているバッファーへのポインター。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedNamespace インターフェイス](isymunmanagednamespace-interface.md)
