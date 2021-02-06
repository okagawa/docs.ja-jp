---
description: '詳細情報: ResolveTypeLib メソッド'
title: ResolveTypeLib メソッド
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
ms.openlocfilehash: ca7f94f630479d30bb9129497b38bcf04e759e5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646284"
---
# <a name="resolvetypelib-method"></a>ResolveTypeLib メソッド

完全修飾パスを返すことにより、タイプライブラリの簡易名を解決します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a>パラメーター  

 `bstrSimpleName`  
 からタイプライブラリの簡易名を格納している [BSTR](/previous-versions/windows/desktop/automat/bstr) 。  
  
 `tlbid`  
 からレジストリのタイプライブラリに割り当てられている GUID。  
  
 `lcid`  
 からタイプライブラリのローカライズ ID。  
  
 `wMajorVersion`  
 からタイプライブラリのメジャーバージョン番号。 たとえば、バージョン *x.y* の場合、メジャーバージョン番号は *x* になります。  
  
 `wMinorVersion`  
 からタイプライブラリのマイナーバージョン番号。 たとえば、バージョン *x.y* の場合、マイナーバージョン番号は *y* になります。  
  
 `syskind`  
 からオペレーティング環境を識別する [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) フラグ。 共通値は SYS_WIN32 と SYS_WIN64 です。  
  
 `pbstrResolvedTlbName`  
 入出力パラメーターで指定されたタイプライブラリの完全パスを格納する [BSTR](/previous-versions/windows/desktop/automat/bstr) へのポインター `bstrSimpleName` 。  
  
## <a name="remarks"></a>解説  

 `ResolveTypeLib`メソッドは[Tlbexp.exe (タイプライブラリエクスポーター)](../../tools/tlbexp-exe-type-library-exporter.md)の処理中に[LoadTypeLibWithResolver 関数](loadtypelibwithresolver-function.md)によって呼び出されます。  
  
 このインターフェイスのカスタム実装では、パラメーターに指定されたタイプライブラリの完全パスを含む [BSTR](/previous-versions/windows/desktop/automat/bstr) を返す必要があり `bstrSimpleName` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Tlf .idl, Tl. h  
  
 **ライブラリ:** Tlf .lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Tlbexp ヘルパー関数](index.md)
- [LoadTypeLibEx](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
