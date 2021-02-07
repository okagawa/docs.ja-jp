---
description: '詳細について: ISymUnmanagedENCUpdate:: InitializeForEnc メソッド'
title: ISymUnmanagedENCUpdate::InitializeForEnc メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.InitializeForEnc
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::InitializeForEnc
helpviewer_keywords:
- ISymUnmanagedENCUpdate::InitializeForEnc method [.NET Framework debugging]
- InitializeForEnc method [.NET Framework debugging]
ms.assetid: 796b2154-b53c-4d07-9e67-80fd6064725a
topic_type:
- apiref
ms.openlocfilehash: 2b70554cc565f025dcf35e2a84523a5f9a6130f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710102"
---
# <a name="isymunmanagedencupdateinitializeforenc-method"></a>ISymUnmanagedENCUpdate::InitializeForEnc メソッド

[ISymUnmanagedENCUpdate:: UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md)メソッドの最初の呼び出しの前にメソッドの境界を計算できるようにします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT InitializeForEnc();  
```  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedENCUpdate インターフェイス](isymunmanagedencupdate-interface.md)
