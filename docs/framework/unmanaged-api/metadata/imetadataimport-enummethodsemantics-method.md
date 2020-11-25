---
title: IMetaDataImport::EnumMethodSemantics メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
ms.openlocfilehash: 3d14aea92633c944d21d867c8152767ae6f1f291
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720972"
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics メソッド

指定したメソッドが関連付けられているプロパティおよびプロパティ変更イベントを列挙します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `phEnum`  
 [入力、出力]列挙子へのポインター。 このメソッドの最初の呼び出しでは、この値は NULL である必要があります。  
  
 `mb`  
 から列挙型のスコープを制限する MethodDef トークン。  
  
 `rEventProp`  
 入出力イベントまたはプロパティを格納するために使用される配列。  
  
 `cMax`  
 [in] `rEventProp` 配列の最大サイズ。  
  
 `pcEventProp`  
 入出力で返されたイベントまたはプロパティの数 `rEventProp` 。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics` 正常に返されました。|  
|`S_FALSE`|列挙するイベントやプロパティはありません。 この場合、 `pcEventProp` は0になります。|  
  
## <a name="remarks"></a>注釈  

 多くの共通言語ランタイム型 *Property* `Changed` では、プロパティイベントとプロパティ `On` *Property* `Changed` に関連するプロパティメソッドが定義されています。 たとえば、型は、 <xref:System.Windows.Forms.Control?displayProperty=nameWithType> <xref:System.Windows.Forms.Control.Font%2A> プロパティ、 <xref:System.Windows.Forms.Control.FontChanged> イベント、およびメソッドを定義し <xref:System.Windows.Forms.Control.OnFontChanged%2A> ます。 プロパティの set アクセサーメソッドは、メソッドを呼び出します。このメソッドは、 <xref:System.Windows.Forms.Control.Font%2A> イベントを発生さ <xref:System.Windows.Forms.Control.OnFontChanged%2A> せ <xref:System.Windows.Forms.Control.FontChanged> ます。 `EnumMethodSemantics` <xref:System.Windows.Forms.Control.OnFontChanged%2A> プロパティとイベントへの参照を取得するには、の MethodDef を使用してを呼び出し <xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control.FontChanged> ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
