---
description: 詳細については、「CorLaunchApplication 関数」を参照してください。
title: CorLaunchApplication 関数
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
ms.openlocfilehash: 89f1f37ddde69fb5ecc24fd9dfd0d0c27d5fac40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716953"
---
# <a name="corlaunchapplication-function"></a>CorLaunchApplication 関数

指定したネットワーク パスのアプリケーションを、指定したマニフェストとその他のアプリケーション データを使用して起動します。  
  
 この関数は .NET Framework 4 で非推奨とされました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `dwClickOnceHost`  
 からアプリケーションを起動しているホストの種類を指定する [HOST_TYPE](host-type-enumeration.md) 列挙体の値。  
  
 `pwzAppFullName`  
 から起動されるアプリケーションの完全な名前。  
  
 `dwManifestPaths`  
 からアプリケーションのマニフェストパスの数。  
  
 `ppwzManifestPaths`  
 から文字列の配列。それぞれが、起動されるアプリケーションのマニフェストへのパスを指定します。  
  
 `dwActivationData`  
 から起動されるアプリケーションのアクティブ化データ項目の数。  
  
 `ppwzActivationData`  
 から文字列の配列。各文字列は、起動されるアプリケーションのアクティベーションデータ項目です。  
  
 `lpProcessInformation`  
 入出力アプリケーションが読み込まれたプロセスに関する情報へのポインター。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](deprecated-clr-hosting-functions.md)
