---
title: ISymUnmanagedENCUpdate::UpdateMethodLines メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateMethodLines
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type:
- apiref
ms.openlocfilehash: 99499b8717f219616b6b368e6393b4b7ca0a79d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699587"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a>ISymUnmanagedENCUpdate::UpdateMethodLines メソッド

再コンパイルされていないが、行が個別に移動したメソッドの行情報を更新できるようにします。 各ステートメントのデルタが許可されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a>パラメーター  

 `mdMethodToken`  
 からメソッドトークンのメタデータ。  
  
 `pDeltas`  
 から `INT32` メソッド内の各シーケンスポイントのデルタを示す値の配列。  
  
 `cDeltas`  
 から `ULONG` パラメーターのサイズを格納している `pDeltas` 。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedENCUpdate インターフェイス](isymunmanagedencupdate-interface.md)
