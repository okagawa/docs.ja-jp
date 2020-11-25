---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPath メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPath
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPath
helpviewer_keywords:
- GetSearchPath method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPath method [.NET Framework debugging]
ms.assetid: b588d470-53c2-4492-be8c-957323eaca0b
topic_type:
- apiref
ms.openlocfilehash: eda8a7ff1d8b3031173bf5f73a8b8a8355e6a62c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705528"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a>ISymUnmanagedSymbolSearchInfo::GetSearchPath メソッド

検索パスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pcchPath`  
 入出力 `ULONG32` 検索パスを格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedSymbolSearchInfo インターフェイス](isymunmanagedsymbolsearchinfo-interface.md)
