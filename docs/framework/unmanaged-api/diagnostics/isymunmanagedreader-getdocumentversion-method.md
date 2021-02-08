---
description: '詳細について: ISymUnmanagedReader:: GetDocumentVersion メソッド'
title: ISymUnmanagedReader::GetDocumentVersion メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
ms.openlocfilehash: e6877a10f0c285186330b320c9b614939f4d9e3f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800202"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a>ISymUnmanagedReader::GetDocumentVersion メソッド

指定したドキュメントの指定したバージョンを取得します。 ドキュメントのバージョンは1から始まり、更新される [たびに増分](isymunmanagedreader-updatesymbolstore-method.md) されます。 パラメーターがの場合は、 `pbCurrent` `true` ドキュメントの最新バージョンです。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pDoc`  
 から指定されたドキュメント。  
  
 `version`  
 入出力指定されたドキュメントのバージョンを受け取る変数へのポインター。  
  
 `pbCurrent`  
 入出力 `true` このがドキュメントの最新バージョンであるかどうか、または最新バージョンでない場合はを受け取る変数へのポインター `false` 。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedReader インターフェイス](isymunmanagedreader-interface.md)
