---
title: ISymUnmanagedDocument::GetCheckSumAlgorithmId メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSumAlgorithmId
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId method [.NET Framework debugging]
- GetCheckSumAlgorithmId method [.NET Framework debugging]
ms.assetid: c7f941cd-e25b-4b85-b1ce-5f77c9208fa9
topic_type:
- apiref
ms.openlocfilehash: 3c82cf45bca3cc9ec73255586db73a903edaf1ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698573"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a>ISymUnmanagedDocument::GetCheckSumAlgorithmId メソッド

チェックサムアルゴリズム識別子を取得します。チェックサムがない場合は、すべての0の GUID を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pRetVal`  
 入出力チェックサムアルゴリズム識別子を受け取る変数へのポインター。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK します。  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedDocument インターフェイス](isymunmanageddocument-interface.md)
