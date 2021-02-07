---
description: '詳細について: ISymUnmanagedBinder3:: GetReaderFromCallback メソッド'
title: ISymUnmanagedBinder3::GetReaderFromCallback メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3.GetReaderFromCallback
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type:
- apiref
ms.openlocfilehash: ba7c819678fee7625f3cddb29d99f5d7f4c6f991
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689873"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a>ISymUnmanagedBinder3::GetReaderFromCallback メソッド

`IID_IDiaReadExeAtRVACallback` `IID_IDiaReadExeAtOffsetCallback` メモリからデバッグディレクトリ情報を取得するために、ユーザーがまたはのいずれかを使用してを実装または提供できるようにします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>パラメーター  

 `importer`  
 からメタデータインポートインターフェイスへのポインター。  
  
 `fileName`  
 からファイル名へのポインター。  
  
 `searchPath`  
 から検索パスへのポインター。  
  
 `searchPolicy`  
 からシンボルリーダーの検索を実行するときに使用するポリシーを指定する [Corsymsearchpolicyattributes](corsymsearchpolicyattributes-enumeration.md) 列挙体の値。  
  
 `callback`  
 からコールバック関数へのポインター。  
  
 `pRetVal`  
 入出力返された [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスに設定されたポインター。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedBinder3 インターフェイス](isymunmanagedbinder3-interface.md)
