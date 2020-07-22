---
title: GetRequestedRuntimeVersion 関数
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
ms.openlocfilehash: b7a38d28b55842e9358bd9c7019b84c529526613
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617166"
---
# <a name="getrequestedruntimeversion-function"></a>GetRequestedRuntimeVersion 関数
指定したアプリケーションによって要求された共通言語ランタイム (CLR) のバージョン番号を取得します。 そのバージョンがインストールされていない場合は、要求されるバージョンより前にインストールされた最も新しいバージョンを取得します。  
  
 この関数は .NET Framework 4 で非推奨とされました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pExe`  
 からアプリケーションの名前。  
  
 `pVersion`  
 入出力正常に完了したときのバージョン番号の文字列を格納するバッファー。  
  
 `cchBuffer`  
 からバージョンバッファーの長さ。  
  
 `pdwLength`  
 入出力バージョン番号文字列の長さへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の値に加えて、Winerror.h で定義されている標準のコンポーネントオブジェクトモデル (COM) エラーコードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|ERROR_INSUFFICIENT_BUFFER|バージョンバッファーが、バージョン文字列を格納するのに十分な大きさではありません。|  
|E_POINTER|`pdwLength` が null です。|  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** Mscoree.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetRequestedRuntimeInfo 関数](getrequestedruntimeinfo-function.md)
- [GetVersionFromProcess 関数](getversionfromprocess-function.md)
- [非推奨の CLR ホスト関数](deprecated-clr-hosting-functions.md)
