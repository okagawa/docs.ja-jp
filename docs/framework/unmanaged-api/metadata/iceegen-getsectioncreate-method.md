---
title: ICeeGen::GetSectionCreate メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
ms.openlocfilehash: 4ef3992d840f539ca07c411c2d740fa32b14edbc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722948"
---
# <a name="iceegengetsectioncreate-method"></a>ICeeGen::GetSectionCreate メソッド

指定された名前とフラグ値を使用して、コードセクションを生成して取得します。  
  
 このメソッドは互換性のために残されています。使用しないでください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `name`  
 から作成するセクションの名前を指定する文字列へのポインター。  
  
 `flags`  
 からオプションを指定するフラグ。  
  
 `section`  
 入出力新しく作成されたコードセクションへのポインター。  
  
## <a name="remarks"></a>注釈  

 `GetSectionCreate`他のメソッドによって処理されない特殊なセクション要件がある場合にのみ、を呼び出します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICeeGen インターフェイス](iceegen-interface.md)
