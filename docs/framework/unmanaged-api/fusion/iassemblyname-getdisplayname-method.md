---
title: IAssemblyName::GetDisplayName メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetDisplayName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type:
- apiref
ms.openlocfilehash: 13d71a9da2539c45076e5eb92e153e37c1df4b47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727914"
---
# <a name="iassemblynamegetdisplayname-method"></a>IAssemblyName::GetDisplayName メソッド

この [IAssemblyName](iassemblyname-interface.md) オブジェクトによって参照されるアセンブリの、人間が判読できる名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `szDisplayName`  
 入出力参照されたアセンブリの名前を格納している文字列バッファー。  
  
 `pccDisplayName`  
 [入力、出力] `szDisplayName` Null 終端文字を含むワイド文字ののサイズ。  
  
 `dwDisplayFlags`  
 からの機能に影響を与える [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) 値のビットごとの組み合わせ `szDisplayName` 。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IAssemblyName インターフェイス](iassemblyname-interface.md)
- [fusion 列挙体](fusion-enumerations.md)
