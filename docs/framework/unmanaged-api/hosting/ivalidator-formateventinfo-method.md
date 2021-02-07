---
description: '詳細情報: IValidator:: FormatEventInfo メソッド'
title: IValidator::FormatEventInfo メソッド
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
ms.openlocfilehash: 28ecf9ab2b14cd2fdd178a4ad9d8e218f7038a9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680162"
---
# <a name="ivalidatorformateventinfo-method"></a>IValidator::FormatEventInfo メソッド

指定した検証エラーに対応するエラーメッセージを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `hVECode`  
 から検証エラーハンドラーに渡された HRESULT 値。  
  
 `Context`  
 から `VEContext` 検証エラーに関するコンテキスト情報を格納しているインスタンス。  
  
 `msg`  
 [入力、出力]返されたエラーメッセージを含む文字列。  
  
 `ulMaxLength`  
 からエラーメッセージの最大長。  
  
 `psa`  
 からエラーを説明する追加のパラメーターを格納しているセーフ配列。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** IValidator、IValidator  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
