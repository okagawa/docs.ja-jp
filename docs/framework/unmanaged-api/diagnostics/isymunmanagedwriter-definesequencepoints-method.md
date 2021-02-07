---
description: '詳細については、次を参照してください: ISymUnmanagedWriter::D efineSequencePoints メソッド'
title: ISymUnmanagedWriter::DefineSequencePoints メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
ms.openlocfilehash: 0c5ac9854ef341512f58cb1cd63ed7dfcde9962e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762332"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints メソッド

現在のメソッド内のシーケンス ポイントのグループを定義します。 開始行と開始列はそれぞれ、メソッド内のステートメントの開始を定義します。 各終了行と終了列は、メソッド内のステートメントの末尾を定義します。 配列は、オフセットの昇順で並べ替える必要があります。 オフセットは、常にメソッドの先頭からバイト単位で測定されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a>パラメーター  

 `document`  
 からシーケンスポイントが定義されているドキュメントオブジェクト。  
  
 `spCount`  
 から、、 `ULONG32` `offsets` `lines` `columns` 、 `endLines` 、および `endColumns` の各バッファーのサイズを示す。  
  
 `offsets`  
 からメソッドの先頭から計測されたシーケンスポイントのオフセット。  
  
 `lines`  
 からシーケンスポイントの開始行番号。  
  
 `columns`  
 からシーケンスポイントの開始列番号。  
  
 `endLines`  
 からシーケンスポイントの終了行番号。 このパラメーターは省略可能です。  
  
 `endColumns`  
 からシーケンスポイントの終了列番号。 このパラメーターは省略可能です。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](isymunmanagedwriter-interface.md)
