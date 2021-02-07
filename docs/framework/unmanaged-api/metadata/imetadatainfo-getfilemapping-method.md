---
description: '詳細について: IMetaDataInfo:: GetFileMapping メソッド'
title: IMetaDataInfo::GetFileMapping メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
ms.openlocfilehash: 82a1a23c50a4d8340804f66966933fc6a11e0f8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688482"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping メソッド

マップされたファイルのメモリ領域とマッピングの種類を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppvData`  
 入出力マップされたファイルの先頭へのポインター。  
  
 `pcbData`  
 入出力マップされた領域のサイズ。 がの場合 `pdwMappingType` `fmFlat` 、これはファイルのサイズです。  
  
 `pdwMappingType`  
 入出力マッピングの種類を示す [CorFileMapping](corfilemapping-enumeration.md) 値です。 共通言語ランタイム (CLR) の現在の実装では、常にを返し `fmFlat` ます。 他の値は将来使用するために予約されています。 ただし、その他の値は将来のバージョンまたはサービスリリースで有効になる可能性があるため、常に戻り値を確認する必要があります。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|すべての出力が入力されます。|  
|`E_INVALIDARG`|引数の値として NULL が渡されました。|  
|`COR_E_NOTSUPPORTED`|CLR 実装では、メモリ領域に関する情報を提供できません。 これが発生する理由としては次のようなことが考えられます。<br /><br /> -メタデータスコープがまたはフラグで開かれました `ofWrite` `ofCopyMemory` 。<br />-フラグなしでメタデータスコープが開かれました `ofReadOnly` 。<br />- [IMetaDataDispenser:: OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) メソッドは、ファイルのメタデータ部分のみを開くために使用されました。<br />-ファイルは、ポータブル実行可能 (PE) ファイルではありません。 **注:**  これらの条件は CLR の実装によって異なり、CLR の将来のバージョンでは緩和される可能性があります。|  
  
## <a name="remarks"></a>解説  

 が指すメモリ `ppvData` は、基になるメタデータスコープが開いている間のみ有効です。  
  
 このメソッドを機能させるには、 [IMetaDataDispenser:: OpenScope](imetadatadispenser-openscope-method.md) メソッドを呼び出して、ディスク上のファイルのメタデータをメモリにマップするときに、フラグを指定 `ofReadOnly` し、またはフラグを指定しないようにする必要があり `ofWrite` `ofCopyMemory` ます。  
  
 各スコープでのファイルマッピングの種類の選択は、CLR の特定の実装に固有です。 ユーザーが設定することはできません。 CLR の現在の実装では常にが返され `fmFlat` `pdwMappingType` ますが、これは clr の将来のバージョンまたは特定のバージョンの今後のサービスリリースで変更される可能性があります。 の戻り値は `pdwMappingType` 、型によってレイアウトとオフセットが異なるため、常にでチェックする必要があります。  
  
 3つのパラメーターのいずれかに対して NULL を渡すことはサポートされていません。 このメソッドはを返し `E_INVALIDARG` 、出力はすべて入力されません。 マッピングの種類または領域のサイズを無視すると、プログラムが異常終了する可能性があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataInfo インターフェイス](imetadatainfo-interface.md)
- [CorFileMapping 列挙体](corfilemapping-enumeration.md)
