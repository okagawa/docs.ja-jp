---
description: '詳細情報: IValidator:: Validate メソッド'
title: IValidator::Validate メソッド
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
ms.openlocfilehash: 6df70274a788b949686fe2509b525c5a8b04089c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680019"
---
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate メソッド

指定された移植可能な実行可能 (PE) ファイルまたは MSIL (Microsoft 中間言語) ファイルを検証します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `veh`  
 から `IVEHandler` 検証エラーを処理するインスタンスへのポインター。  
  
 `pAppDomain`  
 からファイルが読み込まれるアプリケーションドメインへのポインター。  
  
 `ulFlags`  
 から実行する必要のある検証を示す、 [Validatorflags](validatorflags-enumeration.md) 値のビットごとの組み合わせ。  
  
 `ulMaxError`  
 から検証を終了するまでに許容されるエラーの最大数。  
  
 `token`  
 から使用しません。  
  
 `fileName`  
 から検証するファイルの名前を指定する文字列。  
  
 `pe`  
 からファイルが格納されているメモリバッファーへのポインター。  
  
 `ulSize`  
 から検証するファイルのサイズ (バイト単位)。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** IValidator、IValidator  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
