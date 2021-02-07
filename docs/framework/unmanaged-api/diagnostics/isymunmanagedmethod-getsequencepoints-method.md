---
description: '詳細について: ISymUnmanagedMethod:: GetSequencePoints メソッド'
title: ISymUnmanagedMethod::GetSequencePoints メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
ms.openlocfilehash: acdfcb014648593065bd1ae252ef936898a1e8b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721295"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints メソッド

このメソッド内のすべてのシーケンスポイントを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a>パラメーター  

 `cPoints`  
 から、、、、、 `ULONG32` およびの各配列のサイズを受け取る `offsets` `documents` `lines` `columns` `endLines` `endColumns` 。  
  
 `pcPoints`  
 入出力 `ULONG32` シーケンスポイントを格納するために必要なバッファーの長さを受け取るへのポインター。  
  
 `offsets`  
 からシーケンスポイントのメソッドの先頭からの MSIL (Microsoft 中間言語) オフセットを格納する配列。  
  
 `documents`  
 からシーケンスポイントが配置されているドキュメントを格納する配列。  
  
 `lines`  
 からシーケンスポイントが配置されているドキュメント内の行を格納する配列。  
  
 `columns`  
 からシーケンスポイントが配置されているドキュメント内の列を格納する配列。  
  
 `endLines`  
 からシーケンスポイントが終了するドキュメント内の行の配列。  
  
 `endColumns`  
 からシーケンスポイントが終了するドキュメント内の列の配列。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedMethod インターフェイス](isymunmanagedmethod-interface.md)
