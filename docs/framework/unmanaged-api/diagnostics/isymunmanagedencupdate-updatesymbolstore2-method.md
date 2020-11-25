---
title: ISymUnmanagedENCUpdate::UpdateSymbolStore2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type:
- apiref
ms.openlocfilehash: c68cf632b789a523b19cc78d8d919c2278b1befa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699574"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a>ISymUnmanagedENCUpdate::UpdateSymbolStore2 メソッド

行情報が要件を満たしている場合に、コンパイラがプログラムデータベース (PDB) ストリームから変更されていない関数を省略できるようにします。 正しい行情報は、古い PDB 行情報と、関数内のすべての行に対して1つのデルタで判別できます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pIStream`  
 から行情報を格納している [IStream](/windows/desktop/api/objidl/nn-objidl-istream) へのポインター。  
  
 `pDeltaLines`  
 から変更された行を含む [Symlinedelta](symlinedelta-structure.md) 構造体へのポインター。  
  
 `cDeltaLines`  
 から `ULONG` 変更された行の数を表す。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedENCUpdate インターフェイス](isymunmanagedencupdate-interface.md)
