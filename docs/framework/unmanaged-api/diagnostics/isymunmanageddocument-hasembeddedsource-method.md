---
description: '詳細について: ISymUnmanagedDocument:: HasEmbeddedSource メソッド'
title: ISymUnmanagedDocument::HasEmbeddedSource メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.HasEmbeddedSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::HasEmbeddedSource
helpviewer_keywords:
- HasEmbeddedSource method [.NET Framework debugging]
- ISymUnmanagedDocument::HasEmbeddedSource method [.NET Framework debugging]
ms.assetid: 385fc4d3-365c-4645-b7b0-6c4c5344b79f
topic_type:
- apiref
ms.openlocfilehash: fcab83fea65d9a9e483bff9d2d75714c233718eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710128"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a>ISymUnmanagedDocument::HasEmbeddedSource メソッド

`true`ドキュメントがデバッグシンボルに埋め込まれている場合はを返します。それ以外の場合はを返し `false` ます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pRetVal`  
 入出力ドキュメントにデバッグシンボルに埋め込まれたソースがあるかどうかを示す変数へのポインター。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK します。  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedDocument インターフェイス](isymunmanageddocument-interface.md)
