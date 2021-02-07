---
description: '詳細について: ISymUnmanagedBinder2:: GetReaderForFile2 メソッド'
title: ISymUnmanagedBinder2::GetReaderForFile2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
ms.openlocfilehash: c1a180ceec07c3087150613365acfce646adc34e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689938"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a>ISymUnmanagedBinder2::GetReaderForFile2 メソッド

メタデータインターフェイスとファイル名を指定すると、モジュールに関連付けられているデバッグシンボルを読み取る正しい [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスが返されます。  
  
 このメソッドは、 [ISymUnmanagedBinder:: GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) メソッドよりも、プログラムデータベース (PDB) ファイルをより広範囲に検索します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
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
  
 `pRetVal`  
 入出力返された [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスに設定されたポインター。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="remarks"></a>解説  

 このバージョンのメソッドでは、モジュールの横の右側以外の領域で PDB ファイルを検索できます。 検索ポリシーは、 [Corsymsearchpolicyattributes](corsymsearchpolicyattributes-enumeration.md)を組み合わせることによって制御できます。 たとえば、は、 `AllowReferencePathAccess | AllowSymbolServerAccess` 実行可能ファイルの横にある PDB とシンボルサーバーを検索しますが、レジストリに対してクエリを実行したり、実行可能ファイルのパスを使用したりしません。 パラメーターを `searchPath` 指定すると、これらのディレクトリは常に検索されます。  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedBinder2 インターフェイス](isymunmanagedbinder2-interface.md)
- [GetReaderForFile メソッド](isymunmanagedbinder-getreaderforfile-method.md)
