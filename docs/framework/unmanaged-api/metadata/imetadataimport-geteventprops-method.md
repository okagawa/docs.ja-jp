---
description: '詳細について: IMetaDataImport:: GetEventProps メソッド'
title: IMetaDataImport::GetEventProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
ms.openlocfilehash: 2680c48254ce7386a1a070667896aecd3bfac100
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789217"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps メソッド

宣言する型、デリゲートの add メソッドおよび remove メソッド、すべてのフラグおよびその他の関連データを含む、指定したイベントトークンによって表されるイベントのメタデータ情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,
   [out] LPCWSTR       szEvent,
   [in]  ULONG         cchEvent,
   [out] ULONG         *pchEvent,
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,
   [out] mdMethodDef   *pmdRemoveOn,
   [out] mdMethodDef   *pmdFire,
   [out] mdMethodDef   rmdOtherMethod[],
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ev`  
 からメタデータを取得するイベントを表すイベントメタデータトークン。  
  
 `pClass`  
 入出力イベントを宣言するクラスを表す TypeDef トークンへのポインター。  
  
 `szEvent`  
 入出力によって参照されるイベントの名前 `ev` 。  
  
 `pchEvent`  
 からのワイド文字で要求された長さ `szEvent` 。  
  
 `pdwEventFlags`  
 入出力のワイド文字で返された長さ `szEvent` 。  
  
 `ptkEventType`  
 入出力イベントの種類を表す TypeRef または TypeDef メタデータトークンへのポインター <xref:System.Delegate> 。  
  
 `pmdAddOn`  
 入出力イベントのハンドラーを追加するメソッドを表すメタデータトークンへのポインター。  
  
 `pmdRemoveOn`  
 入出力イベントのハンドラーを削除するメソッドを表すメタデータトークンへのポインター。  
  
 `pmdFire`  
 入出力イベントを発生させるメソッドを表すメタデータトークンへのポインター。  
  
 `rmdOtherMethod`  
 入出力イベントに関連付けられている他のメソッドへのトークンポインターの配列。  
  
 `cMax`  
 [in] `rmdOtherMethod` 配列の最大サイズ。  
  
 `pcOtherMethod`  
 入出力で返されたトークンの数 `rmdOtherMethod` 。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
