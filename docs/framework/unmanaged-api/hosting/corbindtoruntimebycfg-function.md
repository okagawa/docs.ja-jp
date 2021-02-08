---
description: '詳細については、次を参照してください: CorBindToRuntimeByCfg 関数'
title: CorBindToRuntimeByCfg 関数
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
ms.openlocfilehash: c1acf6a8f1d8637bc2d6cd180016ff51cf500107
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790075"
---
# <a name="corbindtoruntimebycfg-function"></a>CorBindToRuntimeByCfg 関数

XML ファイルから読み取られたバージョン情報を使用して、共通言語ランタイム (CLR) をプロセスに読み込みます。  
  
 この関数は .NET Framework 4 で非推奨とされました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,
    [out] LPVOID FAR*  ppv  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pCfgStream`  
 から `IStream` XML ファイルを読み取るオブジェクトへのポインター。  
  
 `reserved`  
 から将来使用するために予約されています。 0 (ゼロ) を値として使用します。  
  
 `startupFlags`  
 からCLR の起動動作を指定する [STARTUP_FLAGS](startup-flags-enumeration.md) 列挙体の値。  
  
 `rclsid`  
 から `CLSID` [ICorRuntimeHost](icorruntimehost-interface.md) または [ICLRRuntimeHost](iclrruntimehost-interface.md) のいずれかのインターフェイスを実装するコクラスの。 サポートされている値は CLSID_CorRuntimeHost と CLSID_CLRRuntimeHost です。  
  
 `riid`  
 から `IID` `ICorRuntimeHost` インターフェイスまたは `ICLRRuntimeHost` インターフェイスの。 サポートされている値は IID_ICorRuntimeHost と IID_ICLRRuntimeHost です。  
  
 `ppv`  
 入出力返されたインターフェイスのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 XML ファイルの形式は、標準のアプリケーション構成ファイルの後にモデル化されています。 XML ファイルの詳細については、「 [構成ファイルのスキーマ](../../configure-apps/file-schema/index.md)」を参照してください。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [CorBindToCurrentRuntime 関数](corbindtocurrentruntime-function.md)
- [CorBindToRuntime 関数](corbindtoruntime-function.md)
- [CorBindToRuntimeEx 関数](corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost 関数](corbindtoruntimehost-function.md)
- [ICorRuntimeHost インターフェイス](icorruntimehost-interface.md)
- [非推奨の CLR ホスト関数](deprecated-clr-hosting-functions.md)
