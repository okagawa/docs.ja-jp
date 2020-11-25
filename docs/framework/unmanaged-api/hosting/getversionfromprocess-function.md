---
title: GetVersionFromProcess 関数
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
ms.openlocfilehash: da0d159da6eef7745c1fa7f7320d5e1355f6e413
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721882"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess 関数

指定したプロセスハンドルに関連付けられている共通言語ランタイム (CLR) のバージョン番号を取得します。  
  
 この関数は .NET Framework 4 で非推奨とされました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `hProcess`  
 からプロセスを処理するハンドル。  
  
 `pVersion`  
 入出力メソッドが正常に完了したときのバージョン番号の文字列を格納するバッファー。  
  
 `cchBuffer`  
 からバージョンバッファーの長さ。  
  
 `pdwLength`  
 入出力バージョン番号文字列の長さへのポインター。  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、次の値に加えて、Winerror.h で定義されている標準のコンポーネントオブジェクトモデル (COM) エラーコードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_INVALIDARG|`pVersion` が null で `cchBuffer` あり、が null ではないか、またはその逆です。<br /><br /> - または -<br /><br /> `hProcess` は、プロセスへの有効なハンドルではありません。<br /><br /> - または -<br /><br /> CLR が読み込まれていません。|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer` が null であるか、またはバージョン文字列の長さを下回っています。|  
|E_NOTIMPL|この方法は、Microsoft Windows 95、Microsoft Windows 98、または Microsoft Windows Millennium Edition オペレーティングシステムでは使用できません。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetRequestedRuntimeInfo 関数](getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion 関数](getrequestedruntimeversion-function.md)
- [非推奨の CLR ホスト関数](deprecated-clr-hosting-functions.md)
