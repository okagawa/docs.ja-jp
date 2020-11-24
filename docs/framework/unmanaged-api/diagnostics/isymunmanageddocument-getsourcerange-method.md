---
title: ISymUnmanagedDocument::GetSourceRange メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
ms.openlocfilehash: f5d7df60a7b9c728b73fe6592226a8b6734b1e66
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95692151"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a>ISymUnmanagedDocument::GetSourceRange メソッド

指定されたバッファーに、埋め込みソースの指定された範囲を返します。 バッファーは、ソースを保持するのに十分な大きさである必要があります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
## <a name="parameters"></a>パラメーター  

 `startLine`  
 から現在のドキュメントの開始行。  
  
 `startColumn`  
 から現在のドキュメントの開始列。  
  
 `endLine`  
 から現在のドキュメントの最終行。  
  
 `endColumn`  
 から現在のドキュメントの最後の列。  
  
 `cSourceBytes`  
 からソースのサイズ (バイト単位)。  
  
 `pcSourceBytes`  
 入出力ソースサイズを受け取る変数へのポインター。  
  
 `source`  
 入出力ソースドキュメントの指定した範囲のサイズと長さ (バイト単位)。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK します。  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedDocument インターフェイス](isymunmanageddocument-interface.md)
