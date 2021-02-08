---
description: '詳細情報: GetTypeLibInfo 関数'
title: GetTypeLibInfo 関数
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
ms.openlocfilehash: 61a830f3ce81345634da377f6fc815a307700e9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794469"
---
# <a name="gettypelibinfo-function"></a>GetTypeLibInfo 関数

指定したタイプライブラリに関する情報を返します。そのためには、その [Tlibattr](/windows/win32/api/oaidl/ns-oaidl-tlibattr) 構造体を調べます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `szFile`  
 からタイプライブラリのファイル名。  
  
 `pTypeLibID`  
 入出力タイプライブラリの GUID。  
  
 `pTypeLibLCID`  
 入出力タイプライブラリのローカライズ ID。  
  
 `pTypeLibPlatform`  
 入出力タイプライブラリのターゲットオペレーティングシステムを識別する [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) フラグ。 共通値は SYS_WIN32 と SYS_WIN64 です。  
  
 `pTypeLibMajorVer`  
 入出力タイプライブラリのメジャーバージョン番号。 たとえば、バージョン *x.y* の場合、メジャーバージョン番号は *x* になります。  
  
 `pTypeLibMinorVer`  
 入出力タイプライブラリのマイナーバージョン番号。 たとえば、バージョン *x.y* の場合、マイナーバージョン番号は *y* になります。  
  
## <a name="remarks"></a>解説  

 `GetTypeLibInfo`関数は、 [Tlbexp.exe (タイプライブラリエクスポーター)](../../tools/tlbexp-exe-type-library-exporter.md)によって呼び出されます。 このツールは、共通言語ランタイム (CLR) アセンブリ内の型を記述するタイプライブラリを生成します。  
  
 いずれかのパラメーターが null の場合、関数はのを返し `HRESULT` `E_POINTER` ます。 それ以外の場合は `S_OK`を返します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Tlf .h  
  
 **ライブラリ:** Tlf .lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Tlbexp ヘルパー関数](index.md)
- [LoadTypeLibEx 関数](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
