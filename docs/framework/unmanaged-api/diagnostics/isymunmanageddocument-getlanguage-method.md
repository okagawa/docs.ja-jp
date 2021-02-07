---
description: '詳細について: ISymUnmanagedDocument:: GetLanguage メソッド'
title: ISymUnmanagedDocument::GetLanguage メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguage
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type:
- apiref
ms.openlocfilehash: f30636303d310ed91aa4229f52a3197a29190d3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710310"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a>ISymUnmanagedDocument::GetLanguage メソッド

このドキュメントの言語識別子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pRetVal`  
 入出力言語識別子を受け取る変数へのポインター。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK します。  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedDocument インターフェイス](isymunmanageddocument-interface.md)
