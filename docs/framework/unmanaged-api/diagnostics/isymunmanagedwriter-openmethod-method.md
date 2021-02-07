---
description: '詳細情報: ISymUnmanagedWriter:: OpenMethod メソッド'
title: ISymUnmanagedWriter::OpenMethod メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
ms.openlocfilehash: 2cf7e6bf7c632449c25a2b49c7658fa7b1cc287e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762228"
---
# <a name="isymunmanagedwriteropenmethod-method"></a>ISymUnmanagedWriter::OpenMethod メソッド

シンボル情報を出力するメソッドを開きます。 指定されたメソッドは、シーケンスポイント、パラメーター、および構文のスコープを定義するための呼び出しの現在のメソッドになります。 メソッド全体を囲む構文の暗黙的なスコープがあります。 以前に閉じられたメソッドを再度開くと、そのメソッドに対して定義されていたシンボルはすべて消去されます。 開いているメソッドは一度に1つしか存在できません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a>パラメーター  

 `method`  
 から開くメソッドのメタデータトークン。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](isymunmanagedwriter-interface.md)
- [CloseMethod メソッド](isymunmanagedwriter-closemethod-method.md)
- [OpenMethod2 メソッド](isymunmanagedwriter3-openmethod2-method.md)
