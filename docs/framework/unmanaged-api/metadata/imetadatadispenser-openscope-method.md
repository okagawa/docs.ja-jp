---
description: '詳細について: IMetaDataDispenser:: OpenScope メソッド'
title: IMetaDataDispenser::OpenScope メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
ms.openlocfilehash: a1fa9a955bfc38ee4b2f23efbe8e492877a3d0c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753615"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope メソッド

ディスク上の既存のファイルを開き、そのメタデータをメモリにマップします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `szScope`  
 から開くファイルの名前。 ファイルには、共通言語ランタイム (CLR) メタデータが含まれている必要があります。  
  
 `dwOpenFlags`  
 から開くためのモード (読み取り、書き込みなど) を指定する [Coropenflags](coropenflags-enumeration.md) 列挙体の値。  
  
 `riid`  
 から返される、必要なメタデータインターフェイスの IID。呼び出し元は、インターフェイスを使用して、メタデータのインポート (読み取り) または出力 (書き込み) を行います。  
  
 の値には `riid` 、"import" インターフェイスまたは "emit" インターフェイスのいずれかを指定する必要があります。 有効な値は、IID_IMetaDataEmit、IID_IMetaDataImport、IID_IMetaDataAssemblyEmit、IID_IMetaDataAssemblyImport、IID_IMetaDataEmit2、または IID_IMetaDataImport2 です。  
  
 `ppIUnk`  
 入出力返されたインターフェイスへのポインター。  
  
## <a name="remarks"></a>解説  

 メタデータのメモリ内コピーは、"import" インターフェイスのいずれかのメソッドを使用してクエリを実行するか、"emit" インターフェイスのいずれかのメソッドを使用してに追加できます。  
  
 ターゲットファイルに CLR メタデータが含まれていない場合、 `OpenScope` メソッドは失敗します。  
  
 .NET Framework バージョン1.0 およびバージョン1.1 では、ofRead に設定してスコープを開くと、 `dwOpenFlags` 共有の対象になります。 つまり、それ以降の呼び出し `OpenScope` で、以前に開いたファイルの名前が渡された場合、既存のスコープが再利用され、新しいデータ構造体のセットは作成されません。 ただし、この共有によって問題が発生する可能性があります。  
  
 .NET Framework バージョン2.0 では、ofRead に設定して開いたスコープ `dwOpenFlags` は共有されなくなりました。 スコープを共有できるようにするには、ofReadOnly 値を使用します。 スコープが共有されると、"読み取り/書き込み" メタデータインターフェイスを使用するクエリは失敗します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataDispenser インターフェイス](imetadatadispenser-interface.md)
- [IMetaDataDispenserEx インターフェイス](imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit インターフェイス](imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport インターフェイス](imetadataassemblyimport-interface.md)
- [IMetaDataEmit インターフェイス](imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](imetadataemit2-interface.md)
- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
